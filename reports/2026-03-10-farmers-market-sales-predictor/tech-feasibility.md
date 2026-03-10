# MarketPrep — Technical Feasibility Report

**Date:** 2026-03-10
**Idea:** A farmers market sales prediction app that integrates with Square POS, pulling historical sales data combined with weather and venue data to predict what vendors should pack for each market day.

---

## Executive Summary

MarketPrep is technically buildable. The core data pipeline — Square Orders API, a weather API, and a lightweight ML forecasting model — is well-supported by existing infrastructure with no fundamental blockers. The primary risks are not API availability but user-side data quality: most small farmers market vendors will have thin transaction histories (fewer than 12 months of usable weekly data), which creates a cold start problem that degrades prediction quality for the majority of early adopters. Square's OAuth flow adds meaningful onboarding friction. The app can reach an MVP state with moderate complexity, but producing predictions that are accurate enough to generate trust will take longer than the MVP phase. Build complexity: **Moderate**. Technical risk score: **7/10**.

---

## Component Breakdown

| Component | Description |
|---|---|
| Square POS Integration | OAuth connection per vendor, Orders API pull of historical transactions by location/date |
| Weather API | Historical weather data matched to past market dates; forecast data for upcoming markets |
| Venue / Market Calendar Data | Market dates, location coordinates, indoor/outdoor flag — no public API exists; must be collected manually or by vendor input |
| Prediction Model | Time-series forecasting at the SKU or category level, per vendor, per market |
| Cold Start Layer | Logic to handle new vendors with little or no history; rule-based or category-average fallback |
| Backend / Data Storage | Store per-vendor historical snapshots, weather joins, model outputs |
| Frontend | Vendor-facing mobile or web UI showing "pack list" recommendations per upcoming market |
| Auth / Multi-tenancy | OAuth token management per vendor; token refresh every 7 days per Square requirements |

---

## Integration Availability Table

| Integration | Exists | Cost Tier | Terms Risk | Notes / Alternatives |
|---|---|---|---|---|
| Square Orders API | Yes | Free (rev share if using Orders API with payments) | Low — explicit seller consent via OAuth | `POST /v2/orders/search` supports location + date range filters; cursor-based pagination; all historical POS transactions accessible |
| Square Webhooks | Yes | Free | Low | `payment.created`, `order.updated`, `inventory.count.updated` all available; sub-60s delivery SLA |
| Open-Meteo (weather) | Yes | Free for non-commercial; donation model | Low | 80+ years of hourly historical data; no API key required; best free option |
| Visual Crossing (weather) | Yes | Free up to 1,000 calls/day; ~$35/month paid | Low | 50+ years of historical data; strong developer docs; recommended for commercial use |
| OpenWeatherMap | Yes | Tiered; free plan available | Low | 47+ years historical; less granular than Visual Crossing for data science use |
| Market venue database | No | N/A | N/A | No public API or dataset for farmers market schedules/locations. Must be built via manual entry, web scraping, or vendor input. USDA has a partial directory but it is not real-time and not API-accessible. |
| Square App Marketplace | Yes (post-approval) | No direct cost; requires 5 active sellers minimum | Low-Moderate | Approval takes up to 14 business days; QA review required; listing accelerates vendor acquisition |

---

## Square API — Detailed Assessment

### Data Available
The `POST /v2/orders/search` endpoint returns full order objects including: line items with catalog item IDs and names, quantities, gross and net sales, timestamps (`created_at`, `closed_at`), payment method, and location ID. This is sufficient to reconstruct historical sales per item per market day.

### Location and Date Filtering
The endpoint supports filtering by `location_ids` array and `date_time_filter` with RFC 3339 timestamps. Pagination is cursor-based. Multiple locations can be queried in one request. This maps cleanly onto the MarketPrep use case: pull all sales from a vendor's market location IDs, filtered by weekend date ranges, paginating through the full history.

### Data Retention
Square does not publish a hard retention window in its documentation. The API implies access to "all of a seller's past sales." One developer forum report noted a 3-month result window in practice, but this appears to be a pagination misconfiguration rather than a platform limit. Treat this as an unconfirmed edge case, not a confirmed blocker — but worth testing early.

### Rate Limits
Square does not publish exact rate limits. Unofficial estimates suggest approximately 10 requests per second per merchant. Batch and search endpoints are recommended to reduce call volume. The app should implement exponential backoff on `429 RATE_LIMITED` responses. For an app that syncs data on a weekly cadence, rate limits are not a practical concern.

### Webhooks
`payment.created` and `order.updated` events are available and deliver in under 60 seconds. Useful for near-real-time sync, though for a market prediction use case, a weekly batch pull is sufficient for the MVP.

### OAuth Requirements
Each vendor must authorize the app individually via Square's OAuth 2.0 flow. Access tokens expire in 30 days; Square requires renewal every 7 days or less. The app must maintain a token management system, surface OAuth status to sellers in a dashboard, and handle token revocation events. This is standard SaaS OAuth plumbing but it is not trivial — a vendor who uninstalls Square or revokes access silently breaks the data pipeline.

Required scopes: `ORDERS_READ`, `MERCHANT_PROFILE_READ`, `PAYMENTS_READ`, `ITEMS_READ`. No elevated or restricted scopes are needed.

### Terms Risk
Square's Developer Terms explicitly prohibit reselling or sublicensing developer tools or API data. MarketPrep uses Square data to generate predictions and present them back to the same merchant who owns the data — this is a permitted use. Aggregating anonymized data across vendors for a benchmark model (e.g., "how do similar vendors perform in rain") would require careful legal review, as this edges toward data reselling. Flag this for counsel before building a cross-vendor benchmark feature.

---

## Weather API — Detailed Assessment

For an MVP, Open-Meteo is the clear choice: free, no API key, 80+ years of hourly historical data, global coverage. For production commercial use, Visual Crossing at ~$35/month provides cleaner developer tooling and explicit commercial licensing.

Weather variables relevant to farmers market prediction:
- Temperature (drives category-level demand shifts documented in research — above 85F boosts fresh produce; below 50F boosts root vegetables and soups)
- Precipitation probability and precipitation amount (rain reduces foot traffic; a 50%+ rain probability is a meaningful predictor of low-attendance days)
- Wind speed (relevant for outdoor stall setup)
- Cloud cover / UV index (secondary signals)

Historical weather can be joined to past market dates by GPS coordinate and date. Forecast weather for the upcoming market date drives the prediction input. The join logic is straightforward: market location coordinate + market date → API call → weather record. No technical blocker here.

---

## ML / Prediction Model — Assessment

### Data Requirements vs. Reality

Industry guidance for time-series sales forecasting:
- Statistical models (exponential smoothing): minimum 12 months
- ML-based models (XGBoost, LightGBM): 18–24 months preferred; ensemble methods perform adequately with fragmented data
- Deep learning (LSTM, Transformer): requires large-scale datasets; not appropriate for per-vendor small data

Farmers market vendors present a structurally challenging forecasting environment:
- Most markets run once or twice per week
- Markets typically operate May–October in most regions (roughly 25–30 selling days per season)
- A vendor with 2 years of Square data has roughly 100–150 usable market-day data points total
- Many vendors are seasonal, meaning 6-month gaps in data are common

At 100–150 data points per vendor with high variance (weather, holidays, market events), a single-vendor model will produce weak predictions. This is not a deal-breaker — it is a constraint that shapes the model architecture.

### Recommended Model Approach for MVP

Given the data constraints, the right approach is not deep learning or per-vendor custom models. The following tiered approach is buildable and defensible:

1. **Rule-based baseline (cold start, 0–6 months of data):** Use vendor category (produce, baked goods, meat, etc.) and weather forecast to apply known demand patterns from research literature. Output is directional ("pack more baked goods, expect 20% lower traffic due to rain"), not precise quantities.

2. **Category-level statistical model (6–18 months):** Apply seasonal decomposition and simple exponential smoothing at the item-category level. Supplement with weather as a feature. This is achievable in Python with `statsmodels` or `prophet`.

3. **Ensemble model (18+ months):** LightGBM or XGBoost with features including: day of season, week number, weather variables, prior-year same-week sales, rolling 4-week average. Research shows ensemble methods outperform statistical methods for fragmented retail data.

4. **Cross-vendor benchmarking (long-term):** Pool anonymized data across vendors in the same category and market size tier to improve predictions for low-history users. Requires legal review of Square's terms before implementation.

### Cold Start Problem

This is the hardest problem for early adoption. A vendor who signs up in week 1 of using MarketPrep has no usable prediction until the app accumulates at least 6 months of their data. Strategies to mitigate:

- Prompt vendors to connect Square during onboarding and immediately backfill historical orders (the Orders API supports this)
- If a vendor has 12+ months of prior Square history, backfill it at signup — this is likely sufficient for a statistical baseline immediately
- For truly new vendors with no Square history, offer category-level averages from similar market contexts as a starting heuristic

The backfill approach is viable because Square historical data is accessible through the Orders API with no documented date floor. A vendor who has used Square for 3 years has 3 years of accessible data.

---

## Data Availability Assessment

| Data Type | Available | Source | Restrictions / Notes |
|---|---|---|---|
| Historical sales by item by date | Yes | Square Orders API (per vendor, OAuth required) | Accessible retroactively at signup; no documented hard retention limit |
| Historical weather by location/date | Yes | Open-Meteo (free) / Visual Crossing (paid) | No restrictions; 50–80 years of hourly data |
| Weather forecast | Yes | Open-Meteo / Visual Crossing / OpenWeatherMap | 7–14 day forecasts available on all plans |
| Farmers market calendar / schedule | No public API | Manual input or scraping required | USDA directory is static and incomplete; no real-time market schedule API exists |
| Venue metadata (indoor/outdoor, size) | No public API | Vendor input at onboarding | Critical variable — indoor vs. outdoor changes weather sensitivity entirely |
| Foot traffic / attendance data | No | None available commercially | Would improve predictions but is not available via any accessible API |

The market calendar gap is the most significant data availability issue. There is no API or clean dataset for farmers market schedules in the US. The app must collect this from vendors during onboarding (market name, dates, location) or scrape individual market websites — a fragile and labor-intensive approach. This is not a blocker but it means data quality depends on vendor cooperation.

---

## Regulatory Flags

No HIPAA or biometrics. No consumer financial data exposure. The relevant considerations are:

- **PCI DSS:** Square handles all payment processing; MarketPrep never touches raw card data. No PCI scope.
- **GDPR / CCPA:** If the app processes customer purchase data (buyer identities attached to orders), there is a GDPR/CCPA consideration for any EU or California users. Square order data does not require buyer identity, and MarketPrep's use case is aggregate/statistical — this is low risk but should be addressed in the privacy policy.
- **Square Developer Terms:** Prohibit reselling or sublicensing data. Cross-vendor aggregation for benchmarking should be reviewed by counsel before shipping.

Overall regulatory burden: low for an MVP focused solely on helping individual vendors see their own data.

---

## Build Complexity Rating: Moderate

**Rationale:**

The Square OAuth integration, token management lifecycle, and historical data backfill pipeline involve real engineering work. The ML prediction layer, even at its simplest, requires decisions about model architecture, feature engineering, and cold start logic that take time to get right. The market calendar data gap requires a manual data collection strategy. None of these are exotic engineering problems, but together they represent 3–5 months of focused development for a small team to reach an MVP.

What makes this Moderate rather than Complex:
- All core APIs exist and are well-documented
- The ML problem is a known class of problem (time-series forecasting with external regressors) with established tooling
- The UI is simple — a vendor sees a table of what to pack for their next market day; this is not a complex UX problem

What prevents it from being Simple:
- OAuth multi-tenancy with token renewal is non-trivial infrastructure
- Cold start handling requires thoughtful product design, not just code
- The ML model produces wrong predictions early; managing vendor trust during the ramp-up period is a real product risk

---

## Hard Blockers

There are no hard blockers that make this idea technically infeasible. The following are near-blockers worth flagging:

1. **No farmers market schedule API.** Market dates and locations must be collected manually. This is a data operations problem that needs a solution before the prediction pipeline can run. Vendors can self-report, but this creates onboarding friction and accuracy risk (e.g., vendors attending multiple markets, or markets changing dates).

2. **Vendor data sparsity.** A significant portion of farmers market vendors are seasonal with fewer than 50 market-day data points in their Square history. Predictions for these vendors will be unreliable. If the app ships predictions before accuracy is defensible, early user trust destruction is a real risk. The app needs a clear "not enough data yet" state rather than confidently wrong outputs.

3. **Square data retention ambiguity.** The Orders API implies full historical access but one developer forum report suggests possible truncation. This needs to be tested with real vendor accounts before committing to a backfill-at-signup architecture.

---

## Dependency Risks

| Dependency | Risk | Severity | Mitigation |
|---|---|---|---|
| Square Orders API | Square changes OAuth requirements, rate limits, or data schema | Medium | Square has a versioned API with a documented lifecycle policy; breaking changes are rare and flagged in changelogs |
| Square App Marketplace | Rejection from marketplace blocks organic distribution | Medium | Marketplace requires 5 active sellers before submission; approval takes 14 business days; plan for direct sales during pre-marketplace phase |
| Square Developer Terms changes | Square restricts cross-vendor data aggregation or increases fees for Orders API usage | Low-Medium | Would kill the benchmark/comparison feature but not the core single-vendor prediction product |
| Weather API (Open-Meteo) | Non-commercial provider changes terms or degrades service | Low | Visual Crossing is a drop-in replacement at ~$35/month; weather data is highly commoditized |
| ML model accuracy | Predictions are wrong often enough to erode vendor trust | High (product risk, not tech) | Mitigate with transparent confidence intervals and a minimum-data threshold before showing predictions |

---

## Comparable Apps That Have Done Similar Integrations

No direct competitor integrates Square + weather + farmers market prediction into a single product (as of available research). The closest comparables are general inventory forecasting tools:

- **Prediko** ($49/month) — AI inventory forecasting for e-commerce, integrates with Shopify; does not integrate with Square or weather data; does not target farmers market vendors
- **StockTrim** ($199/month) — integrates with various POS and e-commerce platforms; general-purpose; no weather layer
- **Inventory Planner by Sage** ($299/month) — integrates with Lightspeed, BigCommerce, Shopify; no Square integration documented; no weather layer

**Cornell Farmers Market Research Project** is the most relevant precedent: they have successfully built an academic pipeline pulling Square data from NY/PA farmers market vendors, joining it with seasonal data, and producing sales analysis and price reports. This is strong proof-of-concept validation that the Square data pipeline is viable at scale (26,000+ transactions analyzed). However, this is a research project, not a commercial product, and it relies on farmers voluntarily sharing Square credentials with a trusted university — a distribution model not replicable for a startup.

None of the existing tools address the specific use case of outdoor market day packing recommendations with weather integration for small vendors. The market gap is real. The technical path is clear.

---

## Recommended MVP Stack

| Layer | Choice | Rationale |
|---|---|---|
| Backend | Python (FastAPI) | Strong ML/data ecosystem; fastapi is lightweight and async-capable for webhook handling |
| Data storage | PostgreSQL | Relational model handles vendor → market → order → item hierarchy cleanly; mature |
| Square integration | Square Python SDK (official) | Official SDK handles OAuth, token refresh, pagination |
| Weather | Open-Meteo (dev/MVP), Visual Crossing (production) | Free for MVP, drop-in upgrade for commercial launch |
| Forecasting | Facebook Prophet or LightGBM | Prophet handles seasonality and missing data well; LightGBM better for feature-rich ensemble as data grows |
| Hosting | Railway or Render | Simple managed hosting; no ops overhead for a two-person team |
| Frontend | React (web) or React Native (mobile) | Web-first for MVP; mobile is valuable but adds scope |

**MVP Scope:** Connect Square via OAuth, backfill historical orders, join with historical weather by market location and date, compute a per-category recommendation for the vendor's next scheduled market (e.g., "you typically sell 40% more baked goods on days above 75F; forecast is 78F, bring 30% more than your average"). Ship this as a read-only dashboard. No mobile app, no real-time sync, no cross-vendor benchmarking.

**Estimated MVP timeline for a two-person technical team:** 10–14 weeks.

---

## Technical Risk Score

**7 / 10** (10 = no technical risk)

The infrastructure exists. The APIs are accessible and well-documented. The forecasting methods are established. The risk is not in the technology — it is in data quality and the cold start trust problem. A vendor who connects the app and receives a bad prediction in week one is a churned user. The build is feasible; the challenge is building enough accuracy, fast enough, on thin vendor data to earn trust before losing it.

---

## Sources

- [Square Orders API Reference](https://developer.squareup.com/reference/square/orders-api)
- [Square SearchOrders Endpoint](https://developer.squareup.com/docs/orders-api/manage-orders/search-orders)
- [Square OAuth API Overview](https://developer.squareup.com/docs/oauth-api/overview)
- [Square OAuth Permissions Reference](https://developer.squareup.com/docs/oauth-api/square-permissions)
- [Square Webhooks Overview](https://developer.squareup.com/docs/webhooks/overview)
- [Square Webhooks Events Reference](https://developer.squareup.com/docs/webhooks/v2webhook-events-tech-ref)
- [Square Developer Terms of Service](https://squareup.com/us/en/legal/general/developers)
- [Square App Marketplace Requirements](https://developer.squareup.com/docs/app-marketplace/requirements)
- [Open-Meteo — Free Weather API](https://open-meteo.com/)
- [Visual Crossing Weather API Pricing](https://www.visualcrossing.com/weather-data-editions/)
- [Best Weather APIs for 2025 — Visual Crossing Blog](https://www.visualcrossing.com/resources/blog/best-weather-api-for-2025/)
- [OpenWeatherMap Pricing](https://openweathermap.org/price)
- [CISA — Selecting a POS System for Your Farm](https://www.buylocalfood.org/selectingpos/)
- [Cornell Farmers Market Research Project](https://farmersmarketresearch.cornell.edu/about/why-use-pos.php)
- [Increasing Customer Purchases at Farmers Markets Using POS Scanner Data (Wiley, 2024)](https://onlinelibrary.wiley.com/doi/10.1002/jaa2.96)
- [Farmers Market Coalition — Square Up Article](https://farmersmarketcoalition.org/square-up/)
- [Best POS Systems for Farmers Markets — POS Nation](https://www.posnation.com/blog/best-pos-system-for-farmers-market)
- [Retail Demand Forecasting — RELEX Solutions](https://www.relexsolutions.com/resources/machine-learning-in-retail-demand-forecasting/)
- [ML-Based Retail Sales Forecasting — SRAnalytics](https://sranalytics.io/blog/retail-demand-forecasting/)
- [Prediko Inventory Forecasting Software](https://www.prediko.io/blog/best-inventory-forecasting-software)
- [Weather and Sales — Esri](https://www.esri.com/about/newsroom/publications/wherenext/using-big-data-to-understand-weather-based-demand-and-optimize-sales)
- [Weather Forecast Farm Marketing — FarmstandApp](https://www.farmstandapp.com/103529/5-ideas-for-incorporating-weather-forecasts-into-farm-marketing/)
- [Farmers Market Statistics 2025 — Seen Markets](https://seenmarkets.com/blog/statistical-analysis-of-farmers-markets-and-craft-fairs)
- [Square API Rate Limit Discussion — Square Developer Forums](https://developer.squareup.com/forums/t/current-square-api-rate-limit/449)
- [Square Handling Errors (Rate Limits)](https://developer.squareup.com/docs/build-basics/general-considerations/handling-errors)
