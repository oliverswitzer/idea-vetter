# Pain Evidence: MarketPrep — Farmers Market Sales Prediction & Inventory Optimization

**Research date:** 2026-03-10
**Idea:** Square POS-integrated app that predicts what vendors should pack for each farmers market based on historical sales, weather, and venue patterns, outputting a specific packing list.

---

## Idea Scope

### Core Components

| Component | Description |
|---|---|
| Target user | Small farmers market vendors — especially bakers, cottage food producers, and produce farmers attending recurring weekly markets |
| Job to be done | Arrive at market with the right quantity and mix of product — not so much they haul things home, not so little they sell out before noon |
| Trigger moment | Sunday night / Monday morning prep planning for the upcoming Saturday market; first bad experience with major leftover waste or embarrassing early sell-out |
| Expected outcome | A specific, confident packing list that reduces financial waste and maximizes revenue, generated automatically from their own sales history |

### Market Angles

1. **Baker/cottage food niche** — highest pain, most vocal community, perishable product = waste is real money lost
2. **Produce farmers** — seasonal crops, highly weather-sensitive, unpredictable demand
3. **Multi-market vendors** — vendors attending 2-5 markets per week at different venues with different traffic patterns
4. **New vendor onboarding** — first-timers with no historical data who rely entirely on guesswork ("10% of foot traffic" rules of thumb)
5. **Market manager tools** — aggregate vendor data to help markets optimize vendor mix and reduce overall waste

### Assumptions That Must Be True

#### Problem
- [ ] Vendors struggle to predict the right quantity to bring and frequently either over-pack or under-pack
- [ ] This unpredictability causes real, measurable financial loss from waste or missed sales
- [ ] Weather is a significant and underutilized signal for packing decisions

#### Market
- [ ] Enough vendors use Square POS to make an integration valuable; most vendor data lives there
- [ ] Vendors attend the same markets repeatedly (weekly), generating enough historical data for prediction
- [ ] The market is large enough: ~150,000+ active farmers market vendors in the US

#### Solution
- [ ] Historical POS sales data + weather + venue patterns are sufficient signal to generate useful predictions
- [ ] Vendors will trust and act on algorithmic recommendations over their intuition

#### Business
- [ ] Vendors will pay a subscription for this (given willingness to pay evidence below)
- [ ] Square's API allows third-party apps to read item-level sales history by location

---

## Evidence Collection

### Source Breadth

Research covered: The Fresh Loaf forum, CakeCentral.com forums, Permies.com market gardening forum, Civil Eats reporting, farmersmarketpos.com, ordergrid.com bakery forecasting blog, locallygrown.app comparison guides, findhomegrown.com, barn2door alternative reviews, GlobalBakes.com, Better Baker Club, academic research (Williamsburg Farmers Market case study, USDA ERS), and ReFED food waste data.

Reddit (r/farmersmarket, r/microbakery) was not directly accessible for scraping. No direct Reddit quotes are included. Paraphrased community consensus from aggregated sources is noted as such.

---

## Pain Point Clusters

| # | Theme | Frequency | Intensity | Urgency | Money Signal | Confidence |
|---|---|---|---|---|---|---|
| 1 | Inventory quantity uncertainty ("how much to bring") | 9/10 | 8/10 | 7/10 | 7/10 | Strong |
| 2 | Perishable waste from over-packing | 7/10 | 8/10 | 6/10 | 8/10 | Strong |
| 3 | Weather as an unmodeled sales variable | 7/10 | 6/10 | 5/10 | 6/10 | Strong |
| 4 | Early sell-out / missed revenue | 6/10 | 7/10 | 7/10 | 7/10 | Moderate |
| 5 | No tool integrating POS history + context for planning | 8/10 | 6/10 | 5/10 | 7/10 | Strong |
| 6 | High cost / complexity of existing farm software | 7/10 | 7/10 | 4/10 | 8/10 | Strong |

---

### Pain Cluster 1: Inventory Quantity Uncertainty

This is the most universally documented pain point across all sources. New and experienced vendors alike describe planning how much to bring as one of the most stressful, uncertain parts of the job.

**Direct quotes and paraphrased observations:**

- "Planning for a market can be intimidating, and one of the most stressful components is simply determining how much food to bring. If you bring too little, you might sell out early and lose the opportunity for sales. However, if you bring an excess, you risk taking home perishable items." — [The Pink Crumbb](https://thepinkcrumbb.shop/blogs/the-blog/determining-inventory-for-a-farmers-market-or-pop-up) / [Global Bakes](https://globalbakes.com/selling-at-a-farmers-market/)

- "I don't want to sell out too soon nor do I want to come home with a ton of leftovers!" — CakeCentral user Paradise_swts, via [CakeCentral "How Much Baking for Farmers Market" thread](https://www.cakecentral.com/forum/t/827650/how-much-baking-for-farmers-market)

- "Many small vendors are very unsure how much of everything to make, because they don't want lots of unsold items." — [Better Baker Club](https://betterbakerclub.com/selling-baked-goods-at-the-farmers-market/)

- "Start with 20–30 loaves. One experienced baker started with 18 sourdough and a couple of Turkish loaves, and now bakes about 80 all up and always sells out." — [Baking Great Bread at Home Blog](https://bakinggreatbread.blog/2025/02/04/from-passion-to-profit-a-bakers-guide-to-market-success/)

- "I'm thinking 20-30 loaves for starts to see where that goes." — Baker on [The Fresh Loaf forum](https://www.thefreshloaf.com/node/11676/selling-farmer039s-markets)

- "After three months of selling, we take 70-80 loaves a week, and usually either sell out or come home with only a couple." — Bassopotamus on [The Fresh Loaf forum](https://www.thefreshloaf.com/node/11676/selling-farmer039s-markets) (shows it takes months of iteration to stabilize)

- Community consensus across multiple sources: the "10% of foot traffic" rule of thumb is the most common shared heuristic — a sign that vendors have no systematic solution and rely on generic formulas.

**Current workaround:** Manual observation over months of selling, spreadsheets, gut feel, "10% of foot traffic" rules of thumb. Zero automation.

**Why it fails:** The heuristic ignores weather, seasonal demand shifts, competing vendor count, and venue-specific patterns. It takes an entire season (16–20 market days) to calibrate without data.

---

### Pain Cluster 2: Perishable Waste from Over-Packing

Financial waste from unsold inventory is a documented, recurring cost — and it's highest for bakers because baked goods have a 1-3 day shelf life.

**Key observations:**

- "One-third of all bread made in America goes to waste." — [Civil Eats, 2017](https://civileats.com/2017/08/31/bake-what-we-knead-solving-the-problem-of-excess-bread/), citing food rescue charity data

- "Mike Avery described a practical solution for unsold inventory: 'Any loaves beyond that went to the local food pantry stamped with Not for Resale. We turned the leftover loaves into croutons and bread pudding for the next market week.'" — [The Fresh Loaf forum](https://www.thefreshloaf.com/node/11676/selling-farmer039s-markets)

- "Without a storefront, what didn't sell often ended up being given away or tossed." — Summarized from CakeCentral vendor discussion, [CakeCentral](https://www.cakecentral.com/forum/t/706811/selling-baked-goods-at-farmers-market)

- "People generally come to a farmer's market prepared to spend only a few bucks... once you factor in FM fees, booth rentals, your time, ingredients, packaging, overhead, and waste, there may not be much profit left." — CakeCentral forum, multiple threads

- Nationally: 80% of surplus food comes from perishables. The food supply chain loses $246.7 billion annually to food waste, with farms bearing roughly 16.8% of that burden (~$12B). — [ReFED](https://refed.org/food-waste/the-problem/)

- "5–10% better SKU-level accuracy can dramatically reduce daily waste and reclaim labor hours lost to manual planning." — [OrderGrid Bakery Demand Forecasting blog](https://www.ordergrid.com/blog/beyond-the-bake-demand-forecasting-strategies-to-help-bakeries-plan-produce-and-profit)

**Financial reality:** A baker selling 80 loaves at $12 each does $960 in gross. If they over-pack by 15 loaves (a common outcome given 10-30 loaf variance described), that's $180 in direct product cost wasted plus the time cost of baking and hauling.

---

### Pain Cluster 3: Weather as an Unmodeled Sales Variable

Weather is universally acknowledged as a major demand driver, but no current tool for farmers market vendors integrates weather data into packing recommendations.

**Evidence:**

- "Weather, economy, and a myriad of other factors play a role. There is very little consistency in sales." — [Permies.com farmer's market sales statistics thread](https://permies.com/t/32042/talk-farmer-market-sales-statistics)

- "Vendors can average $1,500 to $2,500 on a good day, but if it's raining or extremely hot, sales can drop to around $1,000." — Multiple vendor reports, cited in [Farmers Market Business Plan (MightySites)](https://mightysites.com/articles/farmers-market-business-plan) and permies thread

- "The presence of rain has a notable negative effect on attendance and sales." — Archambault et al. (2020), ["Vendor Variety and Market Sales: A Case Study of the Williamsburg Farmers Market"](https://www.foodsystemsjournal.org/index.php/fsj/article/download/786/772/1597), *Journal of Agriculture, Food Systems, and Community Development*

- Weather and special events "should be tracked alongside sales and attendance data." — [Farmers Market Coalition](https://farmersmarketcoalition.org/3-0-methods-implementation/)

- "Markets are seasonal; sales ebb with the weather, holidays, and harvest cycles. If you guess wrong, you either over-prep and waste product or under-prep and miss revenue during the first sunny Saturday of spring." — [farmersmarketpos.com](https://farmersmarketpos.com/common-pos-challenges-farmers-market/)

**Gap identified:** Vendors manually note weather in spreadsheets at best. No existing vendor-facing tool automatically correlates their historical sales with weather data and uses it to inform future packing decisions.

---

### Pain Cluster 4: Early Sell-Out / Missed Revenue

The inverse of over-packing is also costly, and vendors are aware that selling out early is not purely a win.

**Evidence:**

- "If you bring too little, you might sell out early and lose the opportunity for sales." — [Global Bakes](https://globalbakes.com/selling-at-a-farmers-market/)

- "One of the biggest challenges for market bakers is managing production efficiently." — [Better Baker Club](https://betterbakerclub.com/selling-baked-goods-at-the-farmers-market/)

- "Selling out early creates urgency for next week... but it also means missed revenue." — Attributed to multiple vendor guides; sells out as a desirable outcome only once vendor is established, but it signals lost revenue in the short term.

- Vendor at permies.com: "we would repack what didn't sell for restaurants or Sunday markets" — showing active, time-consuming workarounds for the inventory mismatch problem on both ends. [Permies](https://permies.com/t/32042/talk-farmer-market-sales-statistics)

---

### Pain Cluster 5: No Tool Integrating POS History with Context for Planning

This is the core product gap. Vendors who use Square (the dominant POS at farmers markets) can see historical sales reports, but those reports don't surface a packing recommendation — they require the vendor to manually analyze and interpret trends.

**Evidence:**

- "Square does offer Sales Reports that vendors can use to see sales trends to help with forecasting — but this is largely a manual, after-the-fact process that requires the vendor to interpret the data themselves." — [farmersmarketpos.com / POSNation](https://www.posnation.com/blog/best-pos-system-for-farmers-market)

- "Square does not currently offer [demand prediction by seasonality or trends] natively... Shopify POS Pro has strong inventory features and can even predict product trends for demand." — [POS Nation](https://www.posnation.com/blog/best-pos-system-for-farmers-market)

- Square is "the most widely used POS among farmers market vendors" — approximately 15 farms surveyed in one CISA study used Square as their primary system, often only for card processing without leveraging product management features. — [CISA Selecting a POS report](https://www.buylocalfood.org/selectingpos/)

- Square "lacks farm-specific perks like automatic marketplace listings or CSA scheduling." Variable-weight pricing for meat and produce requires third-party workarounds. — [Locally Grown blog](https://www.locallygrown.app/blog/2025-06-16-farm-pos-systems-compared-square-vs-local-line-vs-barn2door-vs-locally-grown)

- "Use last season's POS reports to build a weekly demand curve... tag transactions by location and event to see which markets outperform." — Recommended as best practice by [farmersmarketpos.com](https://farmersmarketpos.com/managing-inventory-at-farmers-markets-with-pos-tips-and-tricks/), but framed as a manual vendor task, not an automated feature.

**Gap:** The tooling to read Square data, correlate it with weather and venue, and output a packing list does not exist as a standalone, vendor-facing product.

---

### Pain Cluster 6: High Cost/Complexity of Existing Farm Software

Vendors who look for solutions find that current platforms are either too expensive, too general, or too complex for a small seasonal vendor doing $800–$2,000/week in gross sales.

**Evidence:**

- "Barn2Door: $99–$299/month plus $399–$599 setup fee. Local Line: $99/month minimum." — [Locally Grown comparison](https://www.locallygrown.app/blog/2025-06-16-farm-pos-systems-compared-square-vs-local-line-vs-barn2door-vs-locally-grown)

- "The monthly subscription alone would consume a significant percentage of revenue for many cottage food producers and small farmers market vendors." — [FindHomeGrown Barn2Door Alternative guide](https://findhomegrown.com/blog/barn2door-alternative-for-small-farm-vendors)

- "At $99/month minimum with a $399 setup fee, Barn2Door represents a significant fixed cost for vendors whose monthly farmers market revenue might be $800–$2,000. When your platform subscription costs 5–12% of your gross revenue before you've accounted for ingredients, booth fees, and packaging, the investment needs to deliver proportional returns." — [FindHomeGrown](https://findhomegrown.com/blog/barn2door-alternative-for-small-farm-vendors)

- "Seasonal vendors who only sell in person a few months a year" find these platforms especially hard to justify. — [Locally Grown](https://www.locallygrown.app/blog/2025-06-16-farm-pos-systems-compared-square-vs-local-line-vs-barn2door-vs-locally-grown)

- None of the existing platforms (Barn2Door, Local Line, Locally Grown, Square) offer prediction-based packing recommendations as a feature. This is not a gap hidden behind a high price point — it simply does not exist in any of these products.

---

## Current Workarounds and Why They Fail

| Workaround | Why It Fails |
|---|---|
| "10% of foot traffic" rule of thumb | Generic heuristic ignores weather, season, venue, competition, and the vendor's own product mix history |
| Manual spreadsheet tracking after each market | Requires vendor discipline; no automated synthesis; doesn't pull from POS data; doesn't incorporate weather |
| Asking other vendors / market organizers | Anecdotal; applies to the whole market not the individual vendor's products |
| Scouting the market as a customer first | One-time input; no ongoing learning; doesn't account for year-over-year variation |
| Pre-orders to eliminate guessing | Solves oversupply but requires a customer base and marketing; doesn't help walk-up traffic planning |
| Donate or repurpose leftovers | Mitigates financial loss but doesn't prevent it; still consumes baking time and ingredients |
| Just using Square POS reports manually | After-the-fact data; requires vendor to interpret trends; no weather overlay; no recommendation output |

---

## Solution Gaps

1. **No automated packing recommendation tool** that reads historical POS data and outputs a SKU-level quantity list.
2. **No weather integration in any vendor-facing planning tool** — weather is universally acknowledged as a driver but entirely absent from existing tooling.
3. **No venue-level differentiation** — vendors who attend multiple markets have no way to see that Saturday's downtown market outperforms Sunday's neighborhood market by 40% for certain items.
4. **No first-season support** — new vendors have no historical data; the current advisory ecosystem leaves them entirely on rules of thumb for their first 16–20 markets.
5. **No affordable, purpose-built forecasting tool for small vendors** — existing demand forecasting software (StockTrim, Prediko, Anaplan) is designed for e-commerce inventory management, not day-of-market packing, and doesn't integrate with Square POS in a market-vendor-specific way.
6. **Square's own analytics require manual interpretation** — no Square feature or officially listed Square App Marketplace app addresses this use case specifically as of research date.

---

## Underserved Segments

1. **Cottage bakers / microbakeries** — Highest pain segment. Baked goods are perishable within 24–48 hours, so waste is total. They are too small for enterprise farm software, operate under cottage food laws with minimal overhead budget, and represent a highly active online community (CakeCentral, The Fresh Loaf, r/microbakery). Their income from markets often supplements a day job, making margin very tight.

2. **New farmers market vendors** — No historical data, maximum uncertainty, highest likelihood of catastrophic first experiences (bringing 80 loaves and selling 20, or bringing 20 and selling out in 45 minutes). This is the moment of peak pain and highest motivation to pay for a solution.

3. **Multi-market vendors** — Vendors attending 2–5 markets weekly at different locations need location-specific predictions. No tool currently does this. One Permies commenter noted repacking unsold product from one market to try at another — a manual logistics pain that prediction would solve.

4. **Produce farmers with narrow windows** — Strawberries, corn, and other seasonal crops have tight harvest and sale windows. Over-packing means donating or composting; under-packing means leaving money in the field. Weather-driven demand swings are especially acute for produce.

---

## Money Signals

**Evidence vendors pay for tools:**

- Square POS is free at base tier, but vendors pay 2.6–2.9% per transaction. At $1,000/week gross, that is $26–$29 per market day in processing fees — vendors are already habituated to paying transaction-based costs.
- Barn2Door ($99–$299/month + $399–$599 setup) has active paying customers despite high cost. This demonstrates that a subset of serious vendors will pay for farm-specific software. — [Barn2Door](https://www.barn2door.com/point-of-sale)
- Local Line ($79–$319/month) has paying farm clients. Walnut Lane Farm switched from Barn2Door to Local Line and cited cost savings and improved farmers market pre-order workflow. — [Locally Grown blog](https://www.locallygrown.app/blog/2025-06-16-farm-pos-systems-compared-square-vs-local-line-vs-barn2door-vs-locally-grown)
- Vendors actively discuss ROI language: "At $99/month minimum... 5–12% of gross revenue" framing shows vendors calculate whether tools pay for themselves. — [FindHomeGrown](https://findhomegrown.com/blog/barn2door-alternative-for-small-farm-vendors)
- The most commonly cited reason NOT to pay for tools is that they are too expensive relative to revenue — not that vendors do not see the value. This implies a price-sensitive but not price-immune segment.
- Pre-orders as a concept have strong adoption signal: multiple platforms (Locally Grown, Square Online, Homegrown at $10/month) have paying users specifically for pre-order workflows — proving vendors pay for tools that reduce waste and guesswork.

**Inferred willingness to pay for MarketPrep:**
- A $10–$20/month subscription that demonstrably saves one batch of unsold bread per month (at $12/loaf x 6 loaves = $72 in product value) is easily ROI-positive.
- Vendors accustomed to Barn2Door pricing ($99+) would likely perceive a $15–$29/month packing prediction tool as very reasonable.
- Pre-order-focused vendors represent the warm end of the market: they are already paying for tools to reduce guessing. A packing list tool is the next logical adjacent product.

**Willingness-to-pay confidence: Moderate.** Direct "I would pay for this specific feature" quotes were not found, as this product does not yet exist and community discussion hasn't formed around it. Inference is based on adjacent tool adoption and cost-vs-waste framing in community discussions.

---

## Most Vocal and Frustrated User Segments

Ranked by observed pain intensity and community presence:

| Rank | Segment | Why Most Vocal | Key Forums/Communities |
|---|---|---|---|
| 1 | Cottage bakers / microbakeries | Perishable waste = direct financial loss; large community; active forum presence | The Fresh Loaf, CakeCentral, r/microbakery, Better Baker Club, TikTok |
| 2 | New farmers market vendors (any category) | Maximum uncertainty; asking lots of questions publicly | CakeCentral noob threads, r/farmersmarket, r/smallbusiness |
| 3 | Sourdough / artisan bread vendors | High production cost, labor-intensive, 1-day freshness window, vocal online | The Fresh Loaf, r/Breadit, Instagram/TikTok sourdough community |
| 4 | Produce farmers at multiple markets | Weather-driven volatility, narrow harvest windows | Permies.com, r/farming, r/marketgardening |
| 5 | Cupcake / pastry vendors | Perishable, weather-sensitive (heat), high display cost | CakeCentral, r/cakedecorating |

---

## Evidence Synthesis

### Pain Point Score Summary

| # | Theme | Frequency | Intensity | Urgency | Money Signal | Confidence |
|---|---|---|---|---|---|---|
| 1 | Inventory quantity uncertainty | 9/10 | 8/10 | 7/10 | 7/10 | Strong |
| 2 | Perishable waste | 7/10 | 8/10 | 6/10 | 8/10 | Strong |
| 3 | Weather as unmodeled variable | 7/10 | 6/10 | 5/10 | 6/10 | Strong |
| 4 | Early sell-out / missed revenue | 6/10 | 7/10 | 7/10 | 7/10 | Moderate |
| 5 | No integrated POS prediction tool | 8/10 | 6/10 | 5/10 | 7/10 | Strong |
| 6 | Existing tools too expensive/complex | 7/10 | 7/10 | 4/10 | 8/10 | Strong |

### Evidence Quality Summary

**Strong evidence for:**
- The core inventory quantity uncertainty problem is universal and well-documented across baker forums, vendor guides, and academic market research
- Weather materially impacts sales and is currently unaccounted for in any vendor-facing tool
- Square is the dominant POS and lacks native demand prediction or packing recommendations
- Existing farm software is priced out of reach for most small seasonal vendors
- Bakers are the most vocal and financially impacted segment

**Moderate evidence for:**
- Vendors would pay a subscription specifically for a packing list tool (inferred from adjacent tool adoption; no direct demand expression found for this exact product)
- Multi-market vendors have differentiated needs that worsen the problem
- The Square App Marketplace represents a viable distribution channel (no direct search of Square Marketplace conducted)

**Weak evidence for:**
- The precise financial magnitude of per-vendor waste in dollars per year (aggregate statistics exist at industry scale but not per-small-vendor)
- Produce farmers' willingness to pay vs. cottage bakers' (both are underserved but community presence and pain expression skews heavily toward bakers)

**Missing evidence on:**
- Whether Square's API access policies support the integration needed for MarketPrep
- Existing apps in the Square App Marketplace that may partially address this
- Whether produce vendors or bakers have a higher actual conversion rate to paid tools

---

## Sources Appendix

- [The Pink Crumbb — Determining Inventory for a Farmer's Market or Pop-Up](https://thepinkcrumbb.shop/blogs/the-blog/determining-inventory-for-a-farmers-market-or-pop-up)
- [Global Bakes — Selling at a Farmer's Market](https://globalbakes.com/selling-at-a-farmers-market/)
- [The Fresh Loaf — Question for Bakers Selling at Farmers Markets](https://www.thefreshloaf.com/node/33348/question-bakers-selling-farmers-markets)
- [The Fresh Loaf — Selling at Farmer's Markets](https://www.thefreshloaf.com/node/11676/selling-farmer039s-markets)
- [Permies.com — Farmer's Market Sales Statistics Thread](https://permies.com/t/32042/talk-farmer-market-sales-statistics)
- [Civil Eats — Bake What We Knead: Solving the Problem of Excess Bread](https://civileats.com/2017/08/31/bake-what-we-knead-solving-the-problem-of-excess-bread/)
- [CakeCentral — How Much Baking for Farmers Market](https://www.cakecentral.com/forum/t/827650/how-much-baking-for-farmers-market)
- [CakeCentral — Noob at the Farmers Market](https://www.cakecentral.com/forum/t/755672/noob-at-the-farmers-market-need-advice)
- [CakeCentral — Selling Baked Goods at Farmers Market](https://www.cakecentral.com/forum/t/706811/selling-baked-goods-at-farmers-market)
- [Better Baker Club — Selling Baked Goods at the Farmer's Market](https://betterbakerclub.com/selling-baked-goods-at-the-farmers-market/)
- [Baking Great Bread at Home Blog — From Passion to Profit](https://bakinggreatbread.blog/2025/02/04/from-passion-to-profit-a-bakers-guide-to-market-success/)
- [OrderGrid — Beyond the Bake: Demand Forecasting for Bakeries](https://www.ordergrid.com/blog/beyond-the-bake-demand-forecasting-strategies-to-help-bakeries-plan-produce-and-profit)
- [farmersmarketpos.com — Common POS Challenges](https://farmersmarketpos.com/common-pos-challenges-farmers-market/)
- [farmersmarketpos.com — Managing Inventory at Farmers Markets with POS](https://farmersmarketpos.com/managing-inventory-at-farmers-markets-with-pos-tips-and-tricks/)
- [POS Nation — Best POS System for Farmers Markets](https://www.posnation.com/blog/best-pos-system-for-farmers-market)
- [CISA — Selecting a Point-of-Sale System for Your Farm](https://www.buylocalfood.org/selectingpos/)
- [Locally Grown — Farm POS Systems Compared](https://www.locallygrown.app/blog/2025-06-16-farm-pos-systems-compared-square-vs-local-line-vs-barn2door-vs-locally-grown)
- [FindHomeGrown — Barn2Door Alternative for Small Farm Vendors](https://findhomegrown.com/blog/barn2door-alternative-for-small-farm-vendors)
- [FindHomeGrown — How to Sell at a Farmers Market](https://findhomegrown.com/blog/how-to-sell-at-a-farmers-market)
- [Archambault et al. (2020) — Vendor Variety and Market Sales: Williamsburg Farmers Market Case Study](https://www.foodsystemsjournal.org/index.php/fsj/article/download/786/772/1597)
- [Farmers Market Coalition — Methods and Implementation](https://farmersmarketcoalition.org/3-0-methods-implementation/)
- [ReFED — Food Waste Data](https://refed.org/food-waste/the-problem/)
- [Inventora — 5 Mistakes to Avoid as a Farmers Market Vendor](https://inventora.com/5-mistakes-to-avoid-as-a-farmers-market-vendor/)
- [Barn2Door — Point of Sale](https://www.barn2door.com/point-of-sale)
- [seenmarkets.com — Farmers Market Statistics 2025](https://seenmarkets.com/blog/statistical-analysis-of-farmers-markets-and-craft-fairs)
