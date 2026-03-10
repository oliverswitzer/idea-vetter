# MarketPrep — Farmers Market Sales Predictor
**Vetting Report | 2026-03-10**

---

## 1. Executive Summary

MarketPrep proposes connecting to a vendor's Square POS and combining historical sales data, weather forecasts, and venue patterns to output a specific packing list for each upcoming farmers market. The problem it solves — "how much should I bring on Saturday?" — is universally documented across baker forums, vendor guides, and academic market research. No current tool addresses it. Every farmers-market-specific app on the App Store sits in Sensor Tower's lowest revenue bucket (<$5k/month), confirming the niche is underfunded, not unneeded. The addressable vendor population is 147,000–438,000 in the US. The Square Orders API fully supports the integration. The clearest wedge is cottage bakers and microbakeries — the highest-pain segment, with perishable product, active online communities, and demonstrated willingness to pay for adjacent tools. The verdict is **niche down and proceed**: the gap is real, the tech is buildable, and distribution via Square App Marketplace plus targeted influencer outreach is actionable. The principal risk is the cold start problem — thin vendor history limits early prediction accuracy.

---

## 2. Verdict

**Niche Down and Proceed.**

Start with cottage bakers and microbakeries. This segment has the highest pain (perishable waste equals total financial loss), the most active online community, and is currently underserved by tools priced at $99–$299/month. A $15–$29/month tool with a clear ROI story — save one bad pack decision per month and the tool pays for itself — is a credible offer for this segment. The overall market ceiling is modest ($17M–$157M ARR), but the gap is unoccupied and the distribution path is specific.

---

## 3. Idea Snapshot

| Dimension | Detail |
|---|---|
| Core user | Small farmers market vendors, primarily cottage bakers and produce farmers |
| Job to be done | Arrive at market with the right quantity and mix — not so much you haul product home, not so little you sell out by 10am |
| Trigger moment | Sunday night prep for Saturday market; first season of painful sell-outs or waste |
| Expected outcome | A specific, auto-generated packing list: "Bring 24 sourdough loaves, 12 chocolate chip dozens, skip the rye" |
| Key assumptions | (1) Vendors struggle to predict quantities and lose money as a result; (2) Square POS history + weather + venue data is sufficient signal; (3) Vendors will pay $15–$29/month for a tool that demonstrably reduces waste |

All three assumptions have supporting evidence. Assumption 3 is the weakest — no direct "I would pay for this" quotes were found for this specific product, though adjacent tool adoption patterns support the inference.

---

## 4. Demand and Trend Signals

| Signal | Finding | Source |
|---|---|---|
| US farmers market industry revenue | $6.3B (2025); 0.6% CAGR for markets but vendor-level gross sales grew 17.38% in 2023 | IBISWorld; Fruit Growers News (2023 Benchmark Survey) |
| Addressable vendor count | 147,000 farms via direct marketing (USDA 2020); ~438,600 vendor slots (8,600 markets × 51 avg vendors) | USDA NASS; USDA 2019 Manager Survey |
| Cloud inventory software | 14.2% CAGR; cloud-based deployments are 65.96% of the market | Grand View Research; Fortune Business Insights |
| AI forecasting, SMB adoption | AI forecasting achieves 92% accuracy vs. 65% traditional; SME SaaS inventory inquiries grew 34% YoY in 2024 | InData Labs; O2b Technologies via trend-researcher |
| Funded competitors | Barn2Door ($19.5M total, $3.1M 2024 revenue) is the only player with meaningful VC backing; no funded startup targets the "what to pack" problem specifically | Latka; PR Web |
| Acquisition window | Seasonal demand spikes February–April (pre-season planning); peak usage June–August | Trend-researcher (inferred from market operating calendar) |
| Square ecosystem | Dominant POS at farmers markets; <20% of vendor payments are now cash; robust third-party API and App Marketplace | USDA; Square Developer docs |

The macro environment is favorable. The specific niche — packing prediction for individual market days — has no funded, focused solution. This is genuine white space, not an overlooked loser.

---

## 5. Competitor Landscape

| App | Positioning | Pricing | Downloads (MoM) | Revenue (MoM) | Strength | Weakness |
|---|---|---|---|---|---|---|
| Barn2Door POS | Full farm e-commerce + in-person POS platform | $99–$299/mo + $399–$599 setup | <5k (Sensor Tower) | <$5k (Sensor Tower) | Real-time inventory sync online/in-person | Crashes at market (2.8/5 stars); no prediction; costs 5–12% of small vendor gross revenue |
| Market Cassa | Simple farmers market cash register, iCloud sync | $9.99 one-time | <5k (Sensor Tower) | <$5k (Sensor Tower) | Low friction entry | No analytics, no prediction, zero reviews |
| FarmersReg2 | SNAP/WIC POS for farmers market vendors | Free | Not found | Not found | EBT/SNAP support | iPad-only; no prediction capability |
| Square POS | Dominant payment processing | Free + 2.6%+$0.15/txn | Millions | N/A | Offline mode; ubiquitous at markets | No demand prediction; requires manual data interpretation for insights |
| Thrive by Shopventory | Multi-location inventory management with Square integration | ~$50–$200/mo (estimated) | Not tracked (web-first) | Not tracked | Deep Square integration; auto-reorder | Not farmers-market-specific; steep setup; targets multi-location retail |
| Local Line | Farm online store + POS | $99+/mo | Not tracked | Not tracked | Weight-based pricing; strong pre-order flow | Prohibitive monthly cost for seasonal vendors; no prediction layer |

**Revenue landscape:** Every farmers-market-specific mobile app sits in Sensor Tower's <$5k/month revenue bucket — the floor of the lowest tier. No standalone vendor app has cracked distribution or willingness to pay at scale. This is ambiguous evidence: the category is either genuinely undersupplied, or vendors are not willing to pay for standalone mobile tools. The pricing gap is clear: $15–$40/month is completely unoccupied between free (Square) and expensive ($99–$299/month platforms).

---

## 6. Pain Points

| # | Theme | Frequency | Intensity | Urgency | Money Signal | Confidence |
|---|---|---|---|---|---|---|
| 1 | Inventory quantity uncertainty ("how much to bring") | 9/10 | 8/10 | 7/10 | 7/10 | Strong |
| 2 | Perishable waste from over-packing | 7/10 | 8/10 | 6/10 | 8/10 | Strong |
| 3 | Weather as an unmodeled sales variable | 7/10 | 6/10 | 5/10 | 6/10 | Strong |
| 4 | Early sell-out / missed revenue | 6/10 | 7/10 | 7/10 | 7/10 | Moderate |
| 5 | No POS-integrated prediction tool | 8/10 | 6/10 | 5/10 | 7/10 | Strong |
| 6 | Existing tools too expensive/complex | 7/10 | 7/10 | 4/10 | 8/10 | Strong |

**Cluster 1 — Inventory quantity uncertainty** is the most universally documented pain across all sources. "I don't want to sell out too soon nor do I want to come home with a ton of leftovers!" is a direct quote from a CakeCentral vendor and functions as a one-sentence product brief. The workaround — the "10% of foot traffic" rule of thumb — ignores weather, season, venue, competition, and the vendor's own product history. It takes an entire season of iteration (16–20 markets) to calibrate without data. [CakeCentral thread](https://www.cakecentral.com/forum/t/827650/how-much-baking-for-farmers-market); [The Fresh Loaf](https://www.thefreshloaf.com/node/11676/selling-farmer039s-markets)

**Cluster 2 — Perishable waste** is highest for bakers, where a 1-3 day shelf life turns every unsold loaf into a total write-off. One baker noted using 80 loaves as their target quantity — arrived at only after 3 months of market experience. At $12/loaf, a 15-loaf variance is $180 in product cost lost. [Baking Great Bread at Home](https://bakinggreatbread.blog/2025/02/04/from-passion-to-profit-a-bakers-guide-to-market-success/); [Better Baker Club](https://betterbakerclub.com/selling-baked-goods-at-the-farmers-market/)

**Cluster 3 — Weather** is universally acknowledged but nowhere modeled. On a good day, vendors report $1,500–$2,500 in gross sales; on a rainy day, the same vendor might do $1,000. Academic research (Archambault et al., 2020, Williamsburg Farmers Market case study) confirms rain has a statistically significant negative effect on attendance and sales. No vendor-facing tool currently incorporates weather. [farmersmarketpos.com](https://farmersmarketpos.com/common-pos-challenges-farmers-market/); [Archambault et al. 2020](https://www.foodsystemsjournal.org/index.php/fsj/article/download/786/772/1597)

**Cluster 6 — Tool cost** is the most frequently cited reason vendors have not adopted existing farm platforms. Barn2Door's $99/month minimum "would consume 5–12% of gross revenue before accounting for ingredients, booth fees, and packaging" for a typical small vendor. [FindHomeGrown](https://findhomegrown.com/blog/barn2door-alternative-for-small-farm-vendors)

---

## 7. Solution Gaps

1. **No Square-native packing recommendation tool exists.** Square is the dominant POS at farmers markets. It surfaces historical sales data but requires vendors to manually interpret it. No app outputs a SKU-level quantity recommendation for the next market day. [farmersmarketpos.com](https://farmersmarketpos.com/managing-inventory-at-farmers-markets-with-pos-tips-and-tricks/); [POS Nation](https://www.posnation.com/blog/best-pos-system-for-farmers-market)

2. **Weather integration is completely absent from all vendor-facing tools.** Vendors manually note weather in spreadsheets at best. Weather-adjusted recommendations are an immediate differentiation point. [Archambault et al. 2020](https://www.foodsystemsjournal.org/index.php/fsj/article/download/786/772/1597)

3. **Venue-level differentiation does not exist.** Vendors who attend multiple markets have no way to see that their downtown Saturday market consistently outperforms their suburban Sunday market for certain products. [pain-evidence.md synthesis]

4. **New vendor support is entirely absent.** First-season vendors with no historical data are left entirely on "10% of foot traffic" heuristics. A category-level rule-based system for new vendors has no current equivalent. [Inventora](https://inventora.com/5-mistakes-to-avoid-as-a-farmers-market-vendor/)

5. **Affordable, purpose-built forecasting for small vendors does not exist.** General demand forecasting tools (Prediko at $49/month, StockTrim at $199/month) target e-commerce inventory, not outdoor market day packing, and do not integrate with Square. [tech-feasibility.md]

---

## 8. Underserved Segments

**Cottage bakers and microbakeries** — Highest pain, most active community, most financially exposed. Baked goods are perishable within 24–48 hours, so every unsold unit is a total loss. This segment is too small for enterprise farm software and explicitly priced out of $99/month platforms. Forums (The Fresh Loaf, CakeCentral, r/microbakery) are active with inventory planning questions, making community-based distribution viable. Per Forrager, South Street Cookies has "the largest YouTube following by far" among cottage food creators in the US — evidence of an organized, reachable community.

**New farmers market vendors** — Maximum uncertainty, highest motivation to pay for guidance. New vendors have no historical data and face their first season with pure guesswork. This is the moment of peak pain; it is also the acquisition moment. If MarketPrep can be positioned as the tool you set up before your first market season, it captures users before they develop manual habits.

**Multi-market vendors** — Vendors attending 2–5 markets weekly at different locations face location-specific demand patterns that no current tool helps them model. One Permies commenter described repacking unsold product from one market to ship to another — a manual logistics pain that venue-level prediction would eliminate.

**Produce farmers with narrow harvest windows** — Strawberries, corn, and seasonal crops have tight sale windows and significant weather-driven demand swings. Over-packing means waste; under-packing means leaving money in the field. Evidence for willingness to pay from this segment is weaker than for bakers.

---

## 9. Money Signals

| Signal Type | Evidence | Source |
|---|---|---|
| Adjacent tool adoption | Barn2Door has active paying users at $99–$299/month despite explicit cost complaints from small vendors | Barn2Door pricing; FindHomeGrown |
| Transaction fee acceptance | Vendors pay Square 2.6%+$0.15 per transaction without resistance — at $1,000/market, that is $26–$29/day | Square pricing |
| Pre-order tool adoption | Locally Grown, Square Online, Homegrown ($10/month) all have paying users for pre-order workflows specifically designed to reduce waste guessing | Locally Grown blog |
| ROI framing is active | Vendors publicly calculate whether tools pay for themselves — cost-vs-waste analysis is present in community discussions | FindHomeGrown; CakeCentral threads |
| Pricing gap is explicit | $15–$50/month is completely unoccupied between free (Square) and $99+ platforms | App store analysis |
| Sensor Tower revenue | All farmers-market-specific apps: <$5k/month (Sensor Tower data for Barn2Door POS, Market Cassa) | Sensor Tower |

Willingness-to-pay confidence: **Moderate**. No direct "I would pay for this specific feature" quotes exist — this product does not yet exist and community discussion has not formed around it. Inference is based on adjacent tool adoption, the active ROI framing in vendor communities, and the $99/month ceiling that existing tools have demonstrated is achievable. A $15–$29/month price point with a clear savings narrative has a credible path to conversion.

---

## 10. Communities and Channels

**Where vendors gather:**

| Community | Platform | Focus | Notes |
|---|---|---|---|
| The Fresh Loaf | Forum | Artisan baking, farmers market selling | Active inventory planning threads; quality evidence source |
| CakeCentral | Forum | Cottage bakers, market vendors | "How much to bring" threads are high-engagement; active buyer audience |
| r/microbakery | Reddit | Cottage food, market-day operations | Evidence suggests active community; direct scraping not available |
| r/farmersmarket | Reddit | Market vendor operations generally | Active community; mix of consumers and vendors |
| Permies.com | Forum | Market gardening, produce farmers | Good evidence for weather/sales correlation pain |
| Farmers Market Coalition | Organization | Market operators and vendor advocacy | Newsletter and conference touchpoints |

**Influencer outreach targets:**

| Rank | Channel | Subscribers | Engagement Rate | Niche Fit | Contact |
|---|---|---|---|---|---|
| 1 | South Street Cookies (Tanya Clowers) | 115K | ~17% (est.) | Very High — active cottage baker selling at Iowa farmers markets | southstreetcookies.com contact form |
| 2 | Our Wyoming Life (Erin Galloway) | 287K | 8.86% (vidIQ) | Very High — active produce farmer selling at Wyoming markets | No public email; channel contact |
| 3 | Roots and Refuge Farm (Jess Sowards) | 640K | 10.7% (vidIQ) | High — prior farmers market vendor; homestead/food growing audience | rootsandrefuge.com |
| 4 | Marketing Food Online (Damian Roberti) | 167K | 5.2% | High — covers Square POS for food businesses; confirmed email | marketingfoodonline@yahoo.com |
| 5 | Acre Homestead (Becky Jones) | 911K | 7.08% (vidIQ) | Medium-High — large reach; audience skews consumer not vendor | No public email |

Square POS content for farmers market vendors is a currently unoccupied YouTube niche. Content around Square + market planning could generate organic search traffic independent of paid influencer placements. [influencers.md]

---

## 11. MVP Recommendation

**Target segment:** Cottage bakers and microbakeries using Square POS who attend recurring weekly markets.

**Core feature set (3 features for MVP):**

1. **Square OAuth connection and historical backfill.** Connect via Square's official OAuth flow; immediately pull and store all accessible transaction history filtered by market-day dates (weekends) and location IDs. This is the entire data foundation.

2. **Weather-adjusted packing recommendation.** For each upcoming scheduled market, output a per-item quantity recommendation based on rolling averages adjusted for the forecasted weather (rain probability, temperature). Be explicit when confidence is low (fewer than 6 months of data). Use Open-Meteo for MVP (free, no API key); upgrade to Visual Crossing (~$35/month) for production.

3. **Post-market actual vs. predicted log.** After each market, prompt the vendor to enter what they actually sold and what came home. This closes the feedback loop, improves future predictions, and gives vendors a tangible record that builds trust in the tool.

**Pricing model:** $19/month flat rate. The ROI story is clear: save one over-pack event per month (6 loaves × $12 = $72 in product value) and the tool pays for itself four times over.

**First distribution channel:** Square App Marketplace listing (requires 5 active sellers and 14-day approval process). While pursuing listing, acquire the first 5 vendors directly via outreach to South Street Cookies and Our Wyoming Life communities. A single creator video — "how I plan what to bring to the farmers market" — from Tanya Clowers (South Street Cookies) would reach 115K subscribers who are exactly the target buyer.

**Validation metric:** 10 paying users after 60 days. If a vendor has used the packing list for 4 consecutive markets without canceling, the product has demonstrated utility.

**What to not build in MVP:** Mobile app, cross-vendor benchmarking, SNAP/EBT integration, produce-specific workflows, multi-language support. All of these add scope without proving the core hypothesis.

---

## 12. Risks and Anti-Thesis

**Risk 1: Cold start problem destroys early trust. (Severity: High — manageable)**

A vendor who signs up and receives a confidently wrong packing recommendation in week one will churn and tell others. The Square Orders API backfill mitigates this for vendors who have 12+ months of history, but new-to-Square vendors and first-season vendors will have thin data. The app must ship a clear "not enough data yet" state and a transparent confidence indicator rather than projecting false precision. If this is handled well, it is manageable. If the app ships wrong predictions confidently, it is fatal for word-of-mouth in tight communities. [tech-feasibility.md]

**Risk 2: The market is too small to reach meaningful ARR. (Severity: Moderate — real ceiling)**

At 147,000 addressable vendors × $19/month × a realistic 1–3% conversion rate, the potential ARR is roughly $335K–$1M. Even at optimistic assumptions (438,000 vendors, 5% conversion, $25/month), ARR tops out at $6.6M before churn. This is a profitable small business, not a venture-scale outcome. Anyone expecting a $50M ARR trajectory should look elsewhere. This is not fatal for the idea but matters for how it is capitalized and who should build it. [trends.md market size calculations]

**Risk 3: Vendors do not trust algorithmic packing recommendations over intuition. (Severity: Moderate — testable)**

Farmers market vendors often have strong intuition built over years of selling. If the algorithm conflicts with their gut and turns out to be wrong once, they will discard it. The product needs to show its reasoning — "you typically sell 30% more on days above 70F, and forecast is 74F" — not just output a number. Trust is built incrementally. This is a product design risk more than a market risk, and it is directly testable. [pain-evidence.md]

**Risk 4: Square App Marketplace approval is not guaranteed, and organic distribution without it is slow. (Severity: Moderate — manageable)**

The Square App Marketplace requires 5 active sellers and a 14-day approval. If approval is delayed or rejected, distribution falls back to direct outreach, which is slower and more expensive. The mitigation is to pursue the first 10 vendors through influencer partnerships before submitting the marketplace application. [tech-feasibility.md]

**Risk 5: Seasonality creates a churn cliff. (Severity: Moderate — structural)**

Most US farmers markets operate May–October. A vendor who stops attending markets in November has no reason to pay $19/month through February. Annual billing rather than monthly would smooth this, but vendors are likely to resist annual commitments for a new unproven tool. Expect significant seasonal churn until annual billing is proven. Acquisition window is February–April each year; plan marketing spend accordingly. [trends.md]

---

## 13. Final Scorecard

| Dimension | Score | Notes |
|---|---|---|
| Problem severity | 8/10 | Perishable waste and missed revenue are documented, repeated financial pains |
| Frequency | 8/10 | Every market day is a packing decision; most vendors attend weekly |
| Urgency | 7/10 | Acute pre-market; low off-season. Seasonal urgency pattern |
| Willingness to pay | 6/10 | Adjacent tool adoption is strong; no direct demand proof for this exact product |
| Competition pressure | 9/10 | No direct competitor exists; the gap is fully unoccupied |
| Accessibility of customer | 7/10 | Square App Marketplace is a natural channel; baker communities are concentrated and reachable |
| Defensibility potential | 6/10 | Data moat grows over time; switching costs once trained on vendor history; early entrant advantage |
| Speed to MVP | 6/10 | 10–14 weeks for a two-person team; moderate complexity primarily from OAuth + ML pipeline |
| **Overall opportunity** | **7/10** | Real problem, clear gap, buildable tech, modest but real market. Not venture-scale, but a viable focused product. |

---

## 14. Sources Appendix

**Trend and Market Data**
- [IBISWorld — Farmers Markets in the US Industry Analysis, 2024](https://www.ibisworld.com/united-states/market-research-reports/farmers-markets-industry/)
- [IBISWorld — Fruit & Vegetable Markets in the US, 2025](https://www.ibisworld.com/united-states/industry/fruit-vegetable-markets/1045/)
- [USDA ERS — Growth in the number of U.S. farmers markets slows](https://ers.usda.gov/data-products/charts-of-note/chart-detail?chartId=104402)
- [USDA — 2019 National Farmers Market Managers Survey](https://www.usda.gov/about-usda/news/blog/discovering-trends-2019-national-farmers-market-managers-survey)
- [USDA NASS — Local Food Marketing Practices Data, 2020](https://www.nass.usda.gov/Newsroom/archive/2022/04-28-2022.php)
- [Fruit Growers News — Insights from the 2023 Benchmark Survey of Farm Markets](https://fruitgrowersnews.com/article/insights-from-the-2023-benchmark-survey-of-farm-markets/)
- [Grand View Research — Inventory Management Software Market Report, 2033](https://www.grandviewresearch.com/industry-analysis/inventory-management-software-market-report)
- [Fortune Business Insights — Inventory Management Software Market](https://www.fortunebusinessinsights.com/inventory-management-software-market-108589)
- [Mordor Intelligence — Inventory Management Software Market](https://www.mordorintelligence.com/industry-reports/inventory-management-software-market)
- [InData Labs — AI Demand Forecasting in 2025](https://indatalabs.com/blog/ai-demand-forecasting)
- [AgFunder News — US agrifoodtech funding up 14% driven by AI](https://agfundernews.com/us-agrifoodtech-funding-up-14-driven-by-investment-in-ai)
- [Latka — How Barn2Door hit $3.1M revenue in 2024](https://getlatka.com/companies/barn2door#funding)
- [PR Web — Barn2Door secures growth funding from Decathlon Capital](https://www.prweb.com/releases/barn2door-secures-growth-funding-from-decathlon-capital-partners-302184796.html)
- [SeenMarkets — Farmers Market Statistics: Revenue, Growth & Trends (2025)](https://seenmarkets.com/blog/statistical-analysis-of-farmers-markets-and-craft-fairs)

**App Store and Competitor Data**
- [Barn2Door POS — App Store](https://apps.apple.com/us/app/barn2door-point-of-sale-pos/id6444369692)
- [Barn2Door POS — Sensor Tower](https://app.sensortower.com/overview/6444369692?country=US)
- [Market Cassa — App Store](https://apps.apple.com/us/app/market-cassa/id6473692036)
- [Market Cassa — Sensor Tower](https://app.sensortower.com/overview/6473692036?country=US)
- [Barn2Door Pricing](https://www.barn2door.com/pricing)
- [Locally Grown — Farm POS Systems Compared](https://www.locallygrown.app/blog/2025-06-16-farm-pos-systems-compared-square-vs-local-line-vs-barn2door-vs-locally-grown)
- [FindHomeGrown — Barn2Door Alternative for Small Farm Vendors](https://findhomegrown.com/blog/barn2door-alternative-for-small-farm-vendors)
- [farmersmarketpos.com — Managing Inventory at Farmers Markets with POS](https://farmersmarketpos.com/managing-inventory-at-farmers-markets-with-pos-tips-and-tricks/)
- [Inventora — 5 Mistakes to Avoid as a Farmers Market Vendor](https://inventora.com/5-mistakes-to-avoid-as-a-farmers-market-vendor/)
- [POS Nation — Best POS System for Farmers Markets](https://www.posnation.com/blog/best-pos-system-for-farmers-market)
- [Thrive by Shopventory — Capterra](https://www.capterra.com/p/145337/Shopventory/)

**Pain Evidence**
- [CakeCentral — How Much Baking for Farmers Market](https://www.cakecentral.com/forum/t/827650/how-much-baking-for-farmers-market)
- [The Fresh Loaf — Selling at Farmer's Markets](https://www.thefreshloaf.com/node/11676/selling-farmer039s-markets)
- [The Pink Crumbb — Determining Inventory for a Farmer's Market or Pop-Up](https://thepinkcrumbb.shop/blogs/the-blog/determining-inventory-for-a-farmers-market-or-pop-up)
- [Global Bakes — Selling at a Farmer's Market](https://globalbakes.com/selling-at-a-farmers-market/)
- [Better Baker Club — Selling Baked Goods at the Farmer's Market](https://betterbakerclub.com/selling-baked-goods-at-the-farmers-market/)
- [Baking Great Bread at Home Blog — From Passion to Profit](https://bakinggreatbread.blog/2025/02/04/from-passion-to-profit-a-bakers-guide-to-market-success/)
- [Permies.com — Farmer's Market Sales Statistics Thread](https://permies.com/t/32042/talk-farmer-market-sales-statistics)
- [Archambault et al. (2020) — Vendor Variety and Market Sales: Williamsburg Farmers Market Case Study](https://www.foodsystemsjournal.org/index.php/fsj/article/download/786/772/1597)
- [Civil Eats — Bake What We Knead: Solving the Problem of Excess Bread](https://civileats.com/2017/08/31/bake-what-we-knead-solving-the-problem-of-excess-bread/)
- [OrderGrid — Beyond the Bake: Demand Forecasting for Bakeries](https://www.ordergrid.com/blog/beyond-the-bake-demand-forecasting-strategies-to-help-bakeries-plan-produce-and-profit)
- [ReFED — Food Waste Data](https://refed.org/food-waste/the-problem/)
- [CISA — Selecting a Point-of-Sale System for Your Farm](https://www.buylocalfood.org/selectingpos/)
- [Farmers Market Coalition — Methods and Implementation](https://farmersmarketcoalition.org/3-0-methods-implementation/)

**Technical Feasibility**
- [Square Orders API Reference](https://developer.squareup.com/reference/square/orders-api)
- [Square SearchOrders Endpoint](https://developer.squareup.com/docs/orders-api/manage-orders/search-orders)
- [Square OAuth API Overview](https://developer.squareup.com/docs/oauth-api/overview)
- [Square App Marketplace Requirements](https://developer.squareup.com/docs/app-marketplace/requirements)
- [Square Developer Terms of Service](https://squareup.com/us/en/legal/general/developers)
- [Open-Meteo — Free Weather API](https://open-meteo.com/)
- [Visual Crossing Weather API Pricing](https://www.visualcrossing.com/weather-data-editions/)
- [Cornell Farmers Market Research Project](https://farmersmarketresearch.cornell.edu/about/why-use-pos.php)
- [Prediko — AI Inventory Forecasting Software](https://www.prediko.io/blog/best-inventory-forecasting-software)

**Influencers**
- [South Street Cookies — Forrager Podcast episode](https://forrager.com/podcast/tanya-mike-clowers-with-south-street-cookies/)
- [Roots and Refuge Farm — vidIQ Stats](https://vidiq.com/youtube-stats/channel/UCTZN3HhejW1tOiRdLGUCGGA/)
- [Our Wyoming Life — vidIQ Stats](https://vidiq.com/youtube-stats/channel/UCDz_dmieFd0neB_VClG8PzA/)
- [Marketing Food Online — Contact Page](https://marketingfoodonline.com/pages/contact-us)
- [Acre Homestead — vidIQ Stats](https://vidiq.com/youtube-stats/channel/UCIxmWUbe4OZuMDJKIHKwwKg/)
- [Cowboy State Daily — Our Wyoming Life profile](https://cowboystatedaily.com/2025/10/04/x-meet-the-woman-now-sharing-our-wyoming-life-with-the-world/)
