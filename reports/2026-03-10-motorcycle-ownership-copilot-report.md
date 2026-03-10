# VIN-Based Motorcycle Ownership Copilot — Vetting Report

**Date:** March 10, 2026
**Verdict:** Proceed (Narrow Wedge)
**Overall Score:** 7/10

---

## 1. Executive Summary

A VIN-based motorcycle ownership copilot targeting a specific, well-documented pain: riders do not know what oil, filter, chain, or tires fit their bike, and ordering the wrong part is common, costly, and in some cases catastrophic. The core workflow — enter your bike once, get exact consumables specs, a service timeline, and pre-filtered shopping links — does not exist anywhere in the current app market. Every significant competitor is a logbook with reminders. None surface spec data or connect it to a purchase flow.

The evidence for the problem is strong across multiple independent sources: forum threads documenting engine damage from wrong-oil incidents, AMSOIL's product category design built around spec confusion, J&P Cycles Trustpilot complaints about wrong parts despite fitment tools, and ADVRider threads where riders describe maintaining a manual + browser tabs + YouTube searches simultaneously to answer a single service question. The market gap is clean and unoccupied.

The affiliate revenue model is credible at modest scale. RevZilla pays 7% on $250–$275 average orders; at 10K monthly active users completing one service per quarter, affiliate revenue alone approaches $315K/year. The primary risk is data quality: an inaccurate spec published in tight motorcycle communities will destroy trust before the app reaches scale. Launch with 25 models, cite every spec to OEM source, and validate conversion before expanding the database.

**Verdict: Proceed on a narrow wedge.** The gap is real and unoccupied. Start narrow, earn trust on data quality, and grow from affiliate revenue before adding a subscription tier.

---

## 2. Verdict

**Proceed — Narrow Wedge**

The gap between what riders need (exact specs + purchase path) and what exists (generic logbooks) is real and unoccupied. Affiliate economics are favorable and testable without a subscription. The wedge is narrow enough to execute with a small team and wide enough to build a defensible data asset over time.

---

## 3. Idea Snapshot

| Element | Detail |
|---|---|
| Core user | Motorcycle owner doing their own maintenance, or managing their own service schedule |
| Job-to-be-done | Know exactly what service is due and exactly what to buy for this specific bike |
| Trigger moment | New bike purchase, approaching a service interval, spring prep, pre-trip inspection |
| Expected outcome | Correct parts ordered on first attempt; no dealer visit needed to confirm specs |
| Key assumptions | Riders will install an app for spec lookup; affiliate click-through rates support unit economics; spec data can be sourced and verified at scale; users trust the app's accuracy over manual lookup |

---

## 4. Demand and Trend Signals

### Market Size

- US registered motorcycles: approximately 8.8–9.6 million (IIHS, 2023)
- US motorcycle and bike parts market: $6.8 billion in 2024, projected $9.3 billion by 2032 at 4.1% CAGR ([PS Market Research](https://www.psmarketresearch.com/market-analysis/us-motorcycle-bike-parts-market-report))
- Aftermarket parts hold 53.5% share of total parts market — the majority of purchases are not OEM
- Global motorcycle accessories market: $20.1 billion in 2024, projected $33.85 billion by 2034 ([Towards Automotive](https://www.towardsautomotive.com/insights/motorcycle-accessories-market-sizing))
- US motorcycle market overall: $10.48 billion in 2024 ([Grand View Research](https://www.grandviewresearch.com/industry-analysis/us-motorcycle-market))

### Segment Trends

- Overall US motorcycle sales fell 7.6–9.2% in 2025; ADV/adventure bikes continued to climb against the trend
- ADV/adventure motorcycle market: $15.99 billion globally in 2024, projected $27.48 billion by 2035 at 5.04% CAGR ([Precedence Research](https://www.precedenceresearch.com/adventure-motorcycle-market))
- BMW R1300 GS / R1250 GS: 68,000+ units sold globally in 2024 alone
- Cruisers: 38.2% of all registered US motorcycles; touring bikes: 23.5%; street/sport: ~75% of new US sales
- Median rider age: 50+; aging but affluent demographic with high willingness to spend; female riders fastest-growing group
- Asia-Pacific dominates global ownership but skews toward low-displacement commuter bikes with dealer-managed service — a different product proposition

### Segment Search Intensity

| Segment | Search Intensity | Growth Trend | DIY Propensity | Notes |
|---|---|---|---|---|
| ADV / Dual Sport | High | Strongly up | High | Fastest-growing segment; technically engaged |
| Street / Sport | High | Flat | Moderate | Largest volume; 75% of US new sales |
| Cruiser | High | Flat to declining | Low-moderate | H-D community dominant; brand-specific forums |
| Touring | Moderate | Stable | Low | Often dealer-serviced; older demographic |
| Dirt/Off-Road | Moderate | Stable | High | Younger, price-sensitive; hour-based intervals |

ADV/dual-sport has the highest signal-to-noise ratio: fastest-growing in a declining market, technically engaged, high spend on accessories, heavy chain-and-consumables maintenance requirements.

### Seasonal Acquisition Pattern

| Season | Signal |
|---|---|
| March–April | Spring prep, first ride of season, Daytona Bike Week cultural start; parts searches spike. One source recorded normalized search value of 82/100 for motorcycle gear in April. |
| May–August | Sustained peak; active service season |
| August–September | End-of-season service, pre-storage prep |
| December–February | Trough in northern states |
| Year-round | New bike purchase (peak confusion moment) |

Marketing cadence should align with March–April (spring prep) and August–September (pre-storage). The best install moment is immediately after a new bike purchase, when spec uncertainty is highest.

### Search Demand Signals

The following recurring query patterns appear across forums, brand sites, and oil brand content — indicating the dominant intent is uncertainty, not forgetting:

- "what oil does a [year/make/model] take"
- "JASO MA vs MA2 for [bike model]"
- "can I use car oil in my motorcycle"
- "wrong oil in motorcycle wet clutch"
- "what size chain for [bike model]"
- "filter cross reference [bike model]"

AMSOIL maintains a dedicated Motorcycle Lookup Tool and publishes Harley-Davidson-specific cross-reference charts — indicating commercial viability of this lookup use case. Partzilla and RevZilla both publish "what oil to use" blog content that ranks in search. RevZilla's investment in MC Garage maintenance video content is itself a demand signal: a $219M/year retailer subsidizing educational content to drive parts sales.

---

## 5. Competitor Landscape

### App Competitor Table

| App | Platform | Rating | Reviews | Downloads (MoM) | Revenue (MoM) | Pricing | Last Updated | Key Strength | Key Weakness |
|---|---|---|---|---|---|---|---|---|---|
| mo.ride | iOS + Android | 4.4 | 145 (iOS) | Not indexed on ST | Not indexed on ST | Free + EUR 9.90/yr | Jan 2025 | 8,000 bike vehicle database with parts compatibility | Data loss bugs; no purchase flow; requires Motogadget hardware for full value |
| Moto Shed | Android (primarily) | Not listed | Not listed | Not indexed | Not indexed | Free | 2024 | VIN-based NHTSA recall alerts; ad-free; CSV export | Android-first; recall-only; no consumables |
| MotorManage | iOS + Android | No public rating | 0 ratings | Not indexed | Not indexed | Free (2 bikes) / King Plan | Mar 2026 | 45,000 models; offline-first; solid freemium | Just launched Mar 7 2026; no fitment data; no purchase integration |
| Kawasaki RIDEOLOGY | iOS + Android | 1.8 | 83 (iOS) | Not indexed | Negligible | Free (OEM) | Mar 2026 | Official Kawasaki connectivity | Bluetooth failures; 1.8 stars; Kawasaki-only; no consumables |
| Yamaha MyRide | iOS + Android | 4.6 | 1,518 (iOS) | Not indexed | Negligible | Free (OEM) | Jan 2025 | Ride tracking; GPS; lean angle | No maintenance intelligence; no consumables; Yamaha-only |
| Harley-Davidson | iOS + Android | 4.8 | 37,318 (iOS) | 7K/month | <$5K/month | Free (OEM) | Feb 2026 | Brand trust; 4.8 stars; community | H-D only; no oil/filter specs; mapping bugs |
| My Triumph | iOS + Android | Not extracted | Not extracted | Not indexed | Not indexed | Free (OEM) | Active 2025 | VIN registration; service interval tracking | Triumph-only; older VINs not recognized; no consumables |
| MotoMainte | iOS | Not listed | Not listed | Not indexed | Not indexed | Free + $4.99/$9.99 IAP | Not listed | Simple history log | No vehicle database; manual entry; Japan-origin |
| Braap | iOS | 4.8 | 4 ratings | Not indexed | Not indexed | Free + IAP | Nov 2016 (ABANDONED) | Hour-based dirt bike tracking | Abandoned 9+ years ago |
| Motorbike Service | iOS | 1.0 | 2 ratings | Not indexed | Not indexed | Free | 2015 (ABANDONED) | Basic checklist | UI broken; abandoned |
| CycleVIN | VIN history tool | N/A | N/A | N/A | N/A | $25/report | Active | Motorcycle-specific VIN history/theft records | History only; no maintenance spec; no ownership utility post-purchase |
| Cyclepedia | Service manual | N/A | N/A | N/A | N/A | $14.99/yr (Pro) | Active | Full OEM service manual access | Paywalled specs; reader UX, not structured data; no purchase integration |
| RevZilla "Shop Your Ride" | Retail fitment tool | N/A | N/A | N/A | N/A | Free (e-commerce) | Active | Best year/make/model fitment filter in consumer market | Requires knowing what you need; no proactive maintenance layer; no VIN entry |
| AMSOIL MyGarage | Branded utility | N/A | N/A | N/A | N/A | Free | Active | VIN/plate scan for AMSOIL product recommendations | AMSOIL products only; brand-locked; no full service picture |

**The gap that no competitor fills:** No app tells a rider "Your 2019 Yamaha MT-07 takes 3.2L of 10W-40 JASO MA2, a Hiflofiltro HF303 filter, and 520 D.I.D. chain pitch" and links directly to buy those parts. Every competitor either has data without a purchase flow, a purchase flow without data, or neither.

### Revenue Landscape

The entire non-OEM maintenance app category generates negligible direct revenue. Sensor Tower does not actively index motorcycle maintenance apps — they are too small for category charts. The Harley-Davidson OEM app (highest-reviewed entry) generates <$5K/month despite 37K iOS reviews. mo.ride at EUR 9.90/year is the category's price ceiling. This is not evidence that riders won't pay; it is evidence that no one has built something worth paying for.

### OEM App Notable Failures

- **Kawasaki RIDEOLOGY** (1.8/5, 83 reviews): Primary complaints are Bluetooth pairing failures requiring airplane mode workarounds and privacy overreach (background location tracking).
- **Yamaha MyRide** (4.6/5, 1,518 reviews): Best-liked OEM app — focused on ride tracking and lean angle data. Zero consumables intelligence. Top complaints: login issues causing data loss, battery drain.
- **My Triumph**: VIN registration supported, but older VINs not recognized and no consumables data surfaced to user.
- **Harley-Davidson**: 37K+ iOS reviews, 4.8 stars, but generates <$5K/month — a loyalty tool, not a business.

---

## 6. Pain Points

| # | Pain Point | Frequency | Intensity | Urgency | WTP Signal | Confidence |
|---|---|---|---|---|---|---|
| 1 | Uncertainty about exact consumables for this specific bike | 9/10 | 8/10 | 7/10 | 9/10 | Strong |
| 2 | Wrong parts ordered despite using fitment tools | 7/10 | 8/10 | 8/10 | 8/10 | Strong |
| 3 | Information fragmentation (manual + forum + YouTube + notes) | 8/10 | 7/10 | 5/10 | 7/10 | Strong |
| 4 | Maintenance history lost when app is abandoned or OS-updated | 6/10 | 8/10 | 4/10 | 6/10 | Moderate |
| 5 | No maintenance documentation for resale | 5/10 | 6/10 | 5/10 | 6/10 | Moderate |
| 6 | Pre-purchase cost estimation / known issues | 4/10 | 7/10 | 8/10 | 7/10 | Moderate |

### Theme 1: Uncertainty About Exact Consumables

The most documented and highest-signal pain. Appears in every major motorcycle community.

**Evidence:**
- Ninja 400 Riders Forum: New rider used car oil for first 1,200km, did not realize motorcycle oil (JASO MA2) was required. ([Ninja 400 Riders Forum](https://www.ninja400riders.com/threads/accidentally-used-car-oil.7813/))
- Cycle Forums thread "DAMNIT!! I Put in the wrong oil!" — rider used automotive 10W40 instead of 20W50 specification; community fielded the question, confirming this is a recurring scenario. ([Cycle Forums](https://www.cycleforums.com/threads/damnit-i-put-in-the-wrong-oil.22013/))
- MachineryLubrication.com: Rider joined a forum where "everyone had an opinion on which oil was best" and even the parts counter had a different recommendation. Decision deferred to forum consensus, not OEM spec. ([MachineryLubrication.com](https://www.machinerylubrication.com/Read/30732/motorcycle-lubrication))
- AMSOIL built an entire product line (metric motorcycle oil, JASO-rated products) and a dedicated VIN/plate scan lookup around this confusion. A $6B company treating "what oil does my bike take" as a core acquisition channel is strong third-party commercial validation.
- JASO rating confusion (MA vs MA2 vs MB; wet clutch vs dry clutch) is a recurring topic — riders don't know, and getting it wrong damages the clutch. ([Terzo Lubricant](https://terzolubricant.com/en/jaso-ma-vs-ma2-which-oil-for-choose/))

### Theme 2: Wrong Parts Ordered Despite Fitment Tools

**Evidence:**
- Big Dog Motorcycles Forum: Dealer sold wrong oil filter (Twin Cam filter for M8 application). Engine seized at 80 mph on the highway. ([Big Dog Motorcycles Forum](https://www.bigdogbiker.com/threads/this-is-what-happens-when-you-use-the-wrong-oil-filter.82756/))
- Honda CBR 1000RR Forums: Rider sold wrong oil filter by parts store; discovered only after draining all oil. ([1000rr.net](https://www.1000rr.net/threads/what-happens-if-you-use-the-wrong-oil-filter.9481/))
- Harley-Davidson Forums: Longer M8 oil filter physically cannot thread on a Twin Cam engine — documented fitment database error. ([HD Forums](https://www.hdforums.com/forum/2014-2024-touring-models/1411983-new-longer-oil-filter-doesn-t-fit-the-twin-cams.html))
- TriumphRat Forum: Mechanic ordered wrong ignition part twice; four different retailers provided four different part numbers after VIN lookup.
- J&P Cycles Trustpilot: Wrong parts despite fitment check tool — documented and recurring.

### Theme 3: Information Fragmentation

**Evidence:**
- ADVRider forum: "I have to have my manual, email, notes, a couple parts diagrams open from a website somewhere, all with a couple of browser windows and YouTube searches pulled up." The clearest articulation of the problem the copilot concept solves. ([ADVRider](https://www.advrider.com/f/threads/motorcycle-maintenance-app.1570843/))
- Multiple forum users in the same thread fall back to spreadsheets, Google Keep, and paper notebooks — not because they prefer them, but because no digital tool solves the problem adequately.

### Theme 4: Data Loss When App Is Abandoned

**Evidence:**
- ADVRider forum: "Then the app author would not update it to be compatible with newer iPhone operating systems. I should have found a way to back up all the data but did not." ([ADVRider](https://www.advrider.com/f/threads/motorcycle-maintenance-app.1570843/))
- App graveyard is real: Braap last updated November 2016; Motorbike Service last updated 2015 and actively broken. Both still in app stores.
- Yamaha MyRide and Harley-Davidson reviews also cite data loss on reinstall or account lockout.

### Theme 5: Maintenance Documentation for Resale

**Evidence:**
- Pre-purchase checklists uniformly cite maintenance history as primary due-diligence: "If the seller cannot provide these details, that's a red flag." ([Escondido Cycle Center](https://www.teamecc.com/blog/what-to-look-for-when-buying-a-used-motorcycle-a-comprehensive-guide--81166))
- Well-documented bikes retain up to 70% of value; unknown-history bikes lose 15–25% at trade-in.
- **Note:** This is a retention and upsell story, not an acquisition story. No rider installs an app for resale value five years from now.

### Current Workarounds and Why They Fail

| Workaround | Why It Fails |
|---|---|
| OEM owner's manual (PDF or paper) | Contains correct specs but requires the rider to own it, find it, and know which table to read. Non-transferable when bike is sold. |
| Brand-specific forum (TriumphRat, SVRider, ADVRider) | Correct information exists but requires searching, trusting the right respondent, and finding the right thread. Takes 15–30 minutes per question. |
| AMSOIL / RevZilla / Partzilla lookup tools | Brand-biased (AMSOIL steers to AMSOIL), retailer-scoped (only shows in-stock items), or incomplete (does not cover all models or all consumables). |
| Google search | High noise-to-signal ratio. Outdated forum posts, wrong model year content, SEO articles that may not cite OEM specs. |
| Spreadsheet | Captures history but provides no lookup, no spec data, no reminder logic, no purchase integration. |
| Year/make/model filter on parts retailers | Requires knowing what you need. Ambiguous trim variants cause fitment errors. |

---

## 7. Solution Gaps

**Gap 1: VIN to consumables spec to purchase is a missing workflow.** No app completes this sequence. RevZilla's fitment filter is the closest but requires the user to already know what they need. mo.ride has a parts database but no purchase flow. Moto Shed does VIN recall checks but nothing else. The 17-character VIN encodes model year, plant, and trim variant — enough to eliminate the ambiguity that causes fitment errors.

**Gap 2: Spec data is not cited to source.** Every existing app either omits spec data or presents it without attribution. Citing specs to OEM documentation (owner's manual, page number) is an immediate trust differentiator that no competitor has attempted.

**Gap 3: No app connects upcoming service to a pre-filtered shopping cart.** The natural next step after "your chain is due at 12,000 miles" is "here are the correct chain, masterlink, and sprockets for your bike." No app makes that connection.

**Gap 4: Trusted, reliable data permanence.** The graveyard of abandoned apps (Braap 2016, Motorbike Service 2015) creates a legitimate adoption barrier. No tool has built the "your records will survive app updates and ownership changes" promise credibly.

**Gap 5: The pre-purchase research moment is unserved.** CycleVIN ($25/report) provides theft and title history. Nothing provides expected service costs, upcoming service intervals by mileage, and known model-year issues — all combined in a single "should I buy this bike?" view. This is an adjacent wedge for a different customer moment.

**Gap 6: Recall intelligence beyond NHTSA.** Moto Shed checks NHTSA recalls via VIN. Service bulletins (TSBs), OEM recall extensions, and regional recall variations are not surfaced anywhere in the consumer app ecosystem.

---

## 8. Underserved Segments

| Rank | Segment | Pain Level | WTP Signal | Why |
|---|---|---|---|---|
| 1 | ADV/dual-sport riders (KTM, BMW GS, Honda Africa Twin, Triumph Tiger) | High | High | Most technically engaged; fastest-growing segment; high spend; complex service intervals and chain-heavy maintenance; US population 500K–800K active riders |
| 2 | New street bike owners (Yamaha MT series, Ninja 400, CB500, SV650) | High | Moderate | Largest population by volume; peak confusion moment for first-time owners; US addressable population 1M–2M |
| 3 | Out-of-warranty European bike owners (Triumph, Ducati, BMW, Aprilia) | High | High | Expensive bikes; owners avoid dealer rates post-warranty; specs not easily Googleable; US population 300K–500K |
| 4 | Cruiser owners (Harley-Davidson, Indian) | Moderate | High | High spend but frequently dealer-serviced; lower DIY tendency |
| 5 | Dirt/off-road/motocross | Moderate | Moderate | High DIY propensity but price-sensitive; hour-based (not mile-based) service intervals require different logic |

**ADV riders are the beachhead.** Fastest-growing segment in a declining market, highest per-rider spend, most technically engaged. Winning this segment with data accuracy creates word-of-mouth that propagates to street bike owners naturally.

---

## 9. Money Signals

### Affiliate Commerce (Primary Monetization)

| Retailer | 2024 Revenue | Commission Rate | Cookie Duration | Est. AOV |
|---|---|---|---|---|
| RevZilla | $219.8M ([Grips Intelligence](https://gripsintelligence.com/insights/retailers/revzilla.com)) | 7% | 14 days | $250–$275 |
| Partzilla | $63.3–111.5M | ~5% | Varies | $225–$250 |
| J&P Cycles | Significant | 7% | Varies | ~$200+ |
| Twisted Throttle | Meaningful | 9% | 30 days | Varies |
| MotoSport | Meaningful | 5% | Varies | ~$150 |
| Pyramid Parts | Growing | Up to 20% | 30 days | Parts-focused |
| Iron Pony | Meaningful | 12% | Varies | Varies |

**Revenue model math (conservative):**
- 10,000 monthly active users completing 1 service per quarter → 2,500 parts purchases/month
- Average order: $150 (conservative consumables kit)
- RevZilla 7% commission: $10.50/purchase
- Monthly affiliate revenue: **$26,250** | Annual: **~$315,000** at 10K MAU
- At 50K MAU same conversion: **~$1.57M/year** before any subscription tier

The key lever: the app reduces friction by pre-populating exact SKUs. When a rider already knows they need 10W-40 JASO MA2 and HF303 filter, the purchase path from reminder to checkout is nearly frictionless — the highest-converting affiliate scenario.

### Subscription (Secondary Monetization)

The entire motorcycle maintenance app market is currently free or near-free. mo.ride at EUR 9.90/year (~$10.80) is the category ceiling. However, riders demonstrably pay for value: RevZilla average orders $250–$275; Cyclepedia Pro at $14.99/year; Haynes manuals at $35–$50. Plausible subscription price ceiling: $2–$5/month or $20–$40/year.

Subscription triggers worth testing: unlimited garage (>2 bikes), service history export/backup, resale report generation, pre-purchase checker access, TSB alerts beyond NHTSA.

### Commercial Validation Signal

AMSOIL built an entire product line (JASO-specific SKUs) and a dedicated VIN/plate-scan lookup around the "what oil does my bike take?" problem. A $6B company treating this as a core acquisition channel is the strongest possible third-party signal that the confusion is commercially meaningful.

---

## 10. Communities and Channels

### Online Communities

| Community | Platform | Size/Signal | Relevance |
|---|---|---|---|
| r/motorcycles | Reddit | Largest general moto subreddit | High — maintenance questions frequent, answered with uncertainty |
| r/bikewrench | Reddit | Moderate, DIY focus | High — exact audience for spec lookup |
| r/advrider | Reddit | Active | High — ADV riders; technically engaged |
| ADVRider.com | Forum | One of largest moto forums globally | High — best forum signal for WTP; threads confirm problem |
| TriumphRat / SVRider | Brand forums | Active, brand-specific | High — fitment frustration consistent across brands |
| MotorcycleForum.com | Forum | General | High — wrong-parts/wrong-oil incidents documented |
| Harley Owners Group (HOG) | Club | 1M+ members, 1,400 chapters | Moderate — large but brand-specific; often dealer-serviced |

### YouTube Influencer Targets

Ranked by audience fit and engagement rate.

| Rank | Channel | Subscribers | Engagement Rate | Audience Fit | Contact |
|---|---|---|---|---|---|
| 1 | Dork in the Road | 187K | 7.38% | HIGH (ADV/dual-sport) | dork@dorkintheroad.com |
| 2 | Delboy's Garage | 262K | ~18%* | HIGH (maintenance-focused) | moonfleet10@yahoo.co.uk |
| 3 | The Bearded Mechanic | 637K | 5.52% | HIGH (DIY maintenance) | thebeardedmechanic.shop/pages/contact |
| 4 | Bret Tkacs | 172K | 4.98% | HIGH (ADV riding) | brettkacs.com/contact |
| 5 | Big Rock Moto | 488K | 4.94% | HIGH (ADV/off-road) | @bigrockmoto (Instagram) |
| 6 | MotoJitsu | 598K | 5.44% | MEDIUM-HIGH (new riders) | gregory.widmar@gmail.com |
| 7 | CycleCruza | 377K | Not confirmed | MEDIUM (beginner/all-in-one) | CycleCruzaFilms@yahoo.com |
| 8 | Yammie Noob | 1.56M | 4.58% | LOW-MEDIUM (entertainment) | YouTube About page |
| 9 | FortNine | 2.29M | 6.02% | MEDIUM (broad; media-commerce conflict) | fortnine.ca/en/contact |
| 10 | Itchy Boots | 3.25M | 10.26% | LOW-MEDIUM (travel, not DIY) | YouTube About page |

*Delboy's 18% engagement rate sourced from youtubers.me; treat as approximate.

**Do NOT pursue as influencer sponsors:** RevZilla (pursue as commercial/affiliate partner — high conflict of interest risk as Comoto media-commerce hybrid), FortNine (same dynamic), Bikes and Beards (1.26% ER — too low), MotoGeo (inactive).

### Priority Outreach

**Tier 1 — Contact immediately:**
1. **Dork in the Road** — [dork@dorkintheroad.com](mailto:dork@dorkintheroad.com). ADV/dual-sport; 7.38% engagement; direct email; dedicated sponsorship page. Pitch: "Know exactly what your bike needs before every trip."
2. **Delboy's Garage** — [moonfleet10@yahoo.co.uk](mailto:moonfleet10@yahoo.co.uk). Hands-on maintenance content; highest raw engagement; 2 videos/week. Pitch: "The app that tells your viewers exactly which oil, filter, and parts to buy before they start the job."
3. **MotoJitsu** — [gregory.widmar@gmail.com](mailto:gregory.widmar@gmail.com). Direct email confirmed; strong new rider audience; peak confusion persona. Pitch: "New bike, now what? Add your VIN and know your first service."

**Tier 2 — High fit, slightly harder to reach:**
1. **Big Rock Moto** — @bigrockmoto Instagram or Patreon. 488K subs, strong ADV focus, growing fast (14K new subs in last 30 days).
2. **The Bearded Mechanic** — contact form at thebeardedmechanic.shop. Deep wrenching audience; long-form format ideal for integrated placement.
3. **Bret Tkacs** — brettkacs.com/contact. Highly credible ADV expert. Infrequent uploader (2/month); better as a dedicated review than rolling sponsorship.

### B2B Note: RevZilla

Do not approach as an influencer sponsor. Pursue as: (a) affiliate partner via revzilla.com/customer-service-affiliates-and-partnerships, and (b) potential acquirer — Comoto Holdings has the inventory, flywheel, and brand trust to replicate this product. Monitor as a competitive threat; acquisition is a realistic exit.

### Acquisition Strategy

Content-led, community-seeded. Publish accurate, model-specific maintenance guides ("Complete service guide for the 2019 Yamaha MT-07") that rank in search, capture the searcher who has the pain, and convert them to the app. This replicates the funnel RevZilla built for commerce — applied to spec lookup.

---

## 11. Technical Feasibility

### What Is Available for Free

- **NHTSA vPIC API**: Free, no registration, JSON output, supports motorcycles. Decodes 17-digit VINs, provides make/model/year/plant, maps to recall database. ([NHTSA vPIC](https://vpic.nhtsa.dot.gov/api/))
- **NHTSA Recalls API**: `api.nhtsa.gov/recalls/recallsByVehicle` — free, motorcycle-supported. ~3 hours to implement.
- **OEM service manuals**: Honda, Yamaha, Kawasaki, KTM, Triumph all offer free PDF manuals. Labor-intensive but produces verified, trusted data. Correct approach for a focused 25-model launch.

### What Requires Licensed Data

| Source | Cost | Coverage | Accuracy Risk |
|---|---|---|---|
| Teoalida motorcycle database | $330–$425 one-time | 40,000+ models in MySQL/CSV | One developer's aggregation; not OEM-sourced; needs independent verification |
| Vehicle Databases API | Undisclosed; free trial | 40,000+ models; claims service intervals, fluid capacities | JASO rating and filter part numbers not confirmed in documentation |
| ACES/PIES fitment standard | 4–5 figure licensing | Industry standard; covers powersports | Too expensive and complex for early-stage build |
| Manual curation from OEM documentation | Time only | 25 models, impeccably accurate | Slowest but highest trust; correct for MVP |

**Recommendation for MVP:** Manually curate consumables specs for top 25 US models from OEM documentation. Use Teoalida as a rapid expansion path once the data model is validated. Reserve ACES/PIES for later-stage retailer partnerships.

### Parts Affiliate Integration

RevZilla, J&P Cycles, MotoSport, and Twisted Throttle all have active affiliate programs via Impact.com, AvantLink, or direct. Integration is standard affiliate link generation — no API required for MVP.

### Data Quality Risk

This is the single highest technical risk. A wrong oil recommendation can damage a wet clutch or cause catastrophic oil starvation. Data must be verified against OEM documentation before shipping for each model. A visible citation ("Per [Year] [Make] [Model] owner's manual, p. 47") would dramatically increase user trust and is the single highest-leverage trust signal available.

---

## 12. MVP Recommendation

**Target segment:** ADV/dual-sport riders and new street bike owners — specifically those who have just acquired a bike or are approaching their first service interval.

**Core feature set for launch:**
1. Bike lookup by VIN or year/make/model (25-model database: top ADV + popular street bikes by US registration volume)
2. Spec display: oil type, viscosity, capacity, JASO rating; OEM filter number + Hiflofiltro aftermarket equivalent; chain pitch and link count; tire sizes front/rear; valve clearance interval
3. Every spec cited to OEM source (owner's manual, page number) — non-negotiable for trust
4. Service interval tracker: enter current mileage, show next service due with parts needed
5. Pre-filtered affiliate shopping links (RevZilla / J&P Cycles) per consumable, per bike
6. NHTSA recall check via free vPIC API (3-hour build, high-trust signal)
7. Service history log: date, mileage, what was done

**What to exclude from MVP:**
- Pre-purchase checker (different user moment; secondary)
- Multi-bike household management (add in v2)
- Shopping cart aggregation and bundled kits (validate individual links first)
- Subscription tier (launch free; add subscription after proving affiliate conversion)
- TSBs beyond NHTSA

**Pricing model:** Free with affiliate monetization at launch. Introduce $2.99/month or $19.99/year premium tier after 6 months once data accuracy is validated and retention is measurable. Unlock trigger: second bike beyond the first free one.

**Build timeline:** 2–4 weeks as a static web tool; 10–14 weeks for a native iOS/Android app. Start with the web tool.

**First distribution channels:**
1. ADVRider.com forum post (organic, free)
2. Delboy's Garage or Dork in the Road sponsored video (first paid channel)

**Success metrics for validation:**
- 500 active bikes added in 60 days
- Affiliate click-through rate ≥ 5%
- At least 50 affiliate clicks/week
- Zero documented spec accuracy complaints in community forums

---

## 13. Three-Wedge Assessment

### Wedge 1: Maintenance Copilot for Current Owners
**Verdict: Strongest wedge. Start here.**

Evidence strength: Strong. Multiple confirmed pain points (consumables confusion, information fragmentation, wrong parts). Willingness to pay implied by affiliate revenue at parts retailers. Direct, immediate job-to-be-done. MVP is a 2-week data build for 25 models.

### Wedge 2: Pre-Purchase Checker for Buyers
**Verdict: Real pain, weaker starting wedge. Consider as a paid add-on.**

Evidence strength: Moderate. Pre-purchase inspection is stressful; maintenance records absence is a documented red flag. However, the purchase moment is episodic (one per bike), not recurring. CycleVIN already addresses the history/theft side. A free pre-purchase checker can serve as a user acquisition funnel that converts to Wedge 1 after purchase.

### Wedge 3: Ownership Record Keeper for Resale
**Verdict: Weakest standalone wedge. Viable as a feature within Wedge 1, not as a lead product.**

Evidence strength: Moderate. Service history is cited in resale contexts; well-documented bikes command better prices. But the install moment ("I want to track for resale later") is weak — no one installs an app five years early for an event that may never happen. Position as a byproduct of Wedge 1 behavior.

---

## 14. Risks and Anti-Thesis

### Risk 1: Data quality is the existential threat

If a published spec is wrong and a rider damages their engine, the failure will be posted immediately across ADVRider, r/bikewrench, and brand forums. These communities are tight, have long memories, and are the primary distribution channel.

**Mitigation:** Cite every spec to OEM source; build a user-reported correction workflow; launch with 25 models rather than 1,000; do not expand coverage until you have independent accuracy verification.

### Risk 2: RevZilla / Comoto could build this

RevZilla has the parts catalog, affiliate infrastructure, brand trust, and engineering resources. A "proactive maintenance layer" added to their REVER navigation app would replicate the core value prop.

**Mitigation:** Speed to launch and depth of spec database are the moat. A neutral, OEM-cited spec tool has a different trust positioning than a retailer-built tool — RevZilla's incentive is to sell parts, not to give neutral spec guidance.

### Risk 3: Experienced riders outgrow the app

The highest-confusion user is a new owner. Once a rider has done three oil changes on the same bike, they no longer need spec lookup. Retention requires expanding value: service history for resale, pre-trip checklists, recall monitoring, multi-bike management.

**Mitigation:** Plan for this at the product roadmap level from day one, not as an afterthought.

### Risk 4: The overall market is not growing

US motorcycle sales declined 7.6–9.2% in 2025. This is a niche product in a contracting market. ADV is growing but cannot offset the broader decline indefinitely.

**Assessment:** Manageable for a niche app. Acquisition by RevZilla, Cycle Gear, or an OEM is a more realistic exit than a Series B.

### Risk 5: Subscription willingness to pay is unproven

The entire non-OEM category is effectively free. mo.ride at EUR 9.90/year is the only data point.

**Mitigation:** Launch with affiliate-only monetization. Do not assume subscription conversion until you have evidence.

### Risk 6: Affiliate attribution leakage

RevZilla's cookie duration is 14 days. A rider who clicks through and completes the purchase after 15+ days loses the commission.

**Mitigation:** Pre-populate shopping carts with exact SKUs to remove reasons to delay purchase; monitor affiliate dashboard; test multi-partner attribution.

### Arguments For

- The market gap is definitively unoccupied — not vaguely.
- The acquisition funnel is SEO-driven and low-cost. Model-specific guides double as organic acquisition and trust-building.
- Affiliate economics are credible and real-time testable. Commission programs exist today.
- The data problem is manageable if scoped correctly. 25 models curated from OEM documentation is a 2-week data build.
- Trust moat: If the app becomes known for accuracy and OEM citation depth, this is sticky. Community trust is cheap to earn and expensive for competitors to replicate.

---

## 15. Final Scorecard

| Dimension | Score | Notes |
|---|---|---|
| Problem severity | 8/10 | Documented engine damage from wrong-oil incidents; AMSOIL built a commercial product category around this exact confusion |
| Frequency | 8/10 | Every service interval creates a lookup event; new-owner confusion is peak frequency |
| Urgency | 6/10 | Rarely time-critical; spring prep and pre-trip are the highest-urgency windows |
| Willingness to pay | 7/10 | $6.8B parts aftermarket validates spend; affiliate model aligns with existing purchase behavior; subscription unproven |
| Competition pressure | 8/10 | No direct competitor for VIN-to-spec-to-purchase workflow; logbook apps are not competing for the same job (10 = low competition) |
| Accessibility of customer | 8/10 | Concentrated in known forums and YouTube channels; ADVRider and r/bikewrench are specific and reachable |
| Defensibility potential | 6/10 | Data asset and OEM citation depth are the moat; no network effects; RevZilla could replicate features |
| Speed to MVP | 7/10 | 2–4 week web tool is realistic; native app requires 10–14 weeks |
| **Overall opportunity** | **7/10** | Real problem, clear gap, viable affiliate economics, manageable risks — worth building as a focused wedge |

---

## 16. Hypothesis Verdicts

**H1: The real pain is "what to buy" (uncertainty), not "forgetting to maintain."**
Confirmed. Forum incidents, oil brand SEO behavior, wrong-filter horror stories, ADVRider fragmentation quote all point to uncertainty at the moment of purchase. Forgetting is solved by a free reminder app. Spec lookup is the defensible moat.

**H2: Riders will trust app fitment/spec data enough to act on it.**
Conditionally confirmed. AMSOIL's VIN-scan tool is a direct analog: riders use it and buy from it. RevZilla's year/make/model filter drives $219M/year in commerce. The trust condition is accuracy — a single documented wrong recommendation would spread quickly.

**H3: Commerce/affiliate monetization beats pure subscription.**
Confirmed as primary. Affiliate programs are live and operational today. Subscription is plausible as a secondary layer but unproven in this category.

**H4: ADV/dual-sport breaks out first.**
ADV/dual-sport is the strongest signal: fastest-growing segment in a declining market, technically engaged, high spend, complex chain-and-consumables maintenance. Modern street bikes (Ninja 400, MT-07, CB500 series) are a strong second: largest raw population, many newer riders with peak uncertainty.

**H5: "Ownership copilot" framing is more durable than "maintenance tracker."**
Supported. "Ownership copilot" implies proactive intelligence, not just logging, and differentiates from every existing competitor. Worth A/B testing against "Your bike's memory" or "service guide for your exact bike" — "copilot" may scan as tech-industry jargon to older riders.

---

## 17. Sources Appendix

| # | Source | URL | Notes |
|---|---|---|---|
| 1 | IIHS: Motorcycles Registered in the US 2002–2023 | https://www.iihs.org/api/datastoredocument/bibliography/2288 | 8.8M registered US motorcycles |
| 2 | Grand View Research: US Motorcycle Market | https://www.grandviewresearch.com/industry-analysis/us-motorcycle-market | $10.48B US market 2024 |
| 3 | PS Market Research: US Motorcycle & Parts Market | https://www.psmarketresearch.com/market-analysis/us-motorcycle-bike-parts-market-report | $6.8B parts market 2024 |
| 4 | Towards Automotive: Motorcycle Accessories Market | https://www.towardsautomotive.com/insights/motorcycle-accessories-market-sizing | $20.1B global accessories 2024 |
| 5 | Precedence Research: Adventure Motorcycle Market | https://www.precedenceresearch.com/adventure-motorcycle-market | $15.99B ADV market 2024 |
| 6 | Riders Share: ADV Bikes Dominating the Industry | https://www.riders-share.com/blog/article/how-adv-motorcycles-are-taking-over-the-industry | ADV growth against declining overall market |
| 7 | Riders Share: Motorcycle Rider Demographics 2026 | https://www.riders-share.com/blog/article/motorcycle-rider-demographics-market-shift-2026 | Median rider age 50+; female riders fastest-growing |
| 8 | Riders Share: Seasonal Motorcycle Trends | https://www.riders-share.com/blog/article/seasonal-motorcycle-trends | Spring acquisition window data |
| 9 | BikeTeacher: Spring 2025 Google Search Insights | https://www.biketeacher.com/blog-repair/2025/3/27/-whats-trending-in-bike-repair-spring-2025-google-search-insights | Seasonal search data |
| 10 | NHTSA: vPIC API | https://vpic.nhtsa.dot.gov/api/ | Free VIN decode API; motorcycle-supported |
| 11 | NHTSA: Recalls by Vehicle API | https://www.nhtsa.gov/recalls | Free recall lookup API |
| 12 | Teoalida: Motorcycle Database | https://www.teoalida.com/cardatabase/motorcycles/ | $330–$425 one-time; 40K+ models |
| 13 | Vehicle Databases: Motorcycle Data API | https://vehicledatabases.com/motorcycle-data-api | Claims 40K+ models; JASO fields unconfirmed |
| 14 | Auto Care Association: ACES and PIES Standards | https://www.autocare.org/data-standards | Industry fitment standard; 4–5 figure licensing |
| 15 | ADVRider: Motorcycle Maintenance App Thread | https://www.advrider.com/f/threads/motorcycle-maintenance-app.1570843/ | Forum; fragmentation quote; data loss warning; WTP signals |
| 16 | VikingBags: 6 Best Motorcycle Maintenance Apps | https://www.vikingbags.com/blogs/news/6-best-motorcycle-maintenance-apps | Competitive roundup |
| 17 | mo.ride — App Store | https://apps.apple.com/us/app/mo-ride-the-motorcycle-app/id1263923061 | 4.4 stars; 145 iOS reviews; EUR 9.90/yr pricing |
| 18 | MotorManage — App Store | https://apps.apple.com/us/app/motormanage-bike-tracker/id6754518530 | Launched Mar 7 2026; 45K model DB; 0 reviews at analysis time |
| 19 | RIDEOLOGY THE APP — App Store | https://apps.apple.com/us/app/rideology-the-app-motorcycle/id1515050057 | 1.8 stars; Bluetooth failure complaints |
| 20 | Moto Shed — Google Play | https://play.google.com/store/apps/details?id=com.bikeshed.maintenance | VIN-based NHTSA recall alerts; free |
| 21 | Yamaha MyRide — App Store | https://apps.apple.com/us/app/myride-motorcycle-routes/id1255766787 | 4.6 stars; 1,518 iOS reviews |
| 22 | Harley-Davidson — App Store + Sensor Tower | https://apps.apple.com/us/app/harley-davidson/id1292723595 | 37K iOS reviews; <$5K/month revenue |
| 23 | Braap — App Store | https://apps.apple.com/us/app/braap-dirt-bike-maintenance-tracker/id1071179263 | Abandoned Nov 2016 |
| 24 | RevZilla: Shop Your Ride | https://www.revzilla.com/motorcycle-parts | Best fitment UX; no maintenance layer |
| 25 | RevZilla: Affiliate Partnership Program | https://www.revzilla.com/customer-service-affiliates-and-partnerships | 7% commission; 14-day cookie |
| 26 | UpPromote: 15 Best Motorcycle Affiliate Programs | https://uppromote.com/blog/motorcycle-affiliate-programs/ | Multi-program overview incl. Iron Pony 12%, Pyramid Parts 20% |
| 27 | Grips Intelligence: RevZilla Revenue | https://gripsintelligence.com/insights/retailers/revzilla.com | $219.8M ecommerce revenue 2024 |
| 28 | Grips Intelligence: Partzilla Revenue | https://gripsintelligence.com/insights/retailers/partzilla.com | $63.3–111.5M ecommerce revenue |
| 29 | AMSOIL: Motorcycle Lookup Tool | https://www.amsoil.com/lookup/motorcycle/ | Commercial validation of spec confusion problem |
| 30 | AMSOIL Blog: MyGarage | https://blog.amsoil.com/finally-all-your-vehicle-maintenance-records-and-reminders-in-one-place/ | VIN/plate scan for oil recommendations |
| 31 | Terzo Lubricant: JASO MA vs MA2 | https://terzolubricant.com/en/jaso-ma-vs-ma2-which-oil-for-choose/ | JASO confusion documented |
| 32 | Ninja 400 Riders Forum: Accidentally Used Car Oil | https://www.ninja400riders.com/threads/accidentally-used-car-oil.7813/ | Wrong oil incident (1,200km on car oil) |
| 33 | Cycle Forums: DAMNIT!! I Put in the Wrong Oil! | https://www.cycleforums.com/threads/damnit-i-put-in-the-wrong-oil.22013/ | Wrong oil thread; community validation |
| 34 | Big Dog Motorcycles Forum: Engine Seizure at 80mph | https://www.bigdogbiker.com/threads/this-is-what-happens-when-you-use-the-wrong-oil-filter.82756/ | Wrong filter → engine seizure |
| 35 | Honda CBR 1000RR Forums: Wrong Oil Filter | https://www.1000rr.net/threads/what-happens-if-you-use-the-wrong-oil-filter.9481/ | Wrong filter sold at parts store |
| 36 | Harley-Davidson Forums: Longer Filter Doesn't Fit | https://www.hdforums.com/forum/2014-2024-touring-models/1411983-new-longer-oil-filter-doesn-t-fit-the-twin-cams.html | Fitment database error documented |
| 37 | MachineryLubrication.com: Motorcycle Lubrication | https://www.machinerylubrication.com/Read/30732/motorcycle-lubrication | Forum consensus replacing OEM spec lookup |
| 38 | TriumphRat: Mechanic Ordered Wrong Part Twice | https://www.triumphrat.net/threads/mechanic-ordered-the-wrong-part-twice.935274/ | VIN lookup still produced wrong part |
| 39 | J&P Cycles — Trustpilot | https://www.trustpilot.com/review/www.jpcycles.com | Wrong parts despite fitment tool |
| 40 | Escondido Cycle Center: Buying a Used Motorcycle | https://www.teamecc.com/blog/what-to-look-for-when-buying-a-used-motorcycle-a-comprehensive-guide--81166 | Service history as primary due-diligence item |
| 41 | CycleVIN: Motorcycle VIN Check | https://cyclevin.com/motorcycle-vin-report/ | $25/report; theft/title/accident history only |
| 42 | Cyclepedia: Motorcycle VIN Decoder | https://www.cyclepedia.com/motorcycle-vin-decoder/ | Paywalled specs at $14.99/yr |
| 43 | My Triumph App | https://www.triumphmotorcycles.com/owners/my-triumph-app | OEM app; older VINs not recognized |
| 44 | RevZilla: OEM App Comparison | https://www.revzilla.com/common-tread/factory-connection-two-very-different-approaches-to-oem-apps | OEM app landscape analysis |
| 45 | MotorManage iOS Launch Blog | https://motormanage.app/blog/motormanage-motorcycle-app-ios-launch | Mar 7 2026 iOS launch |
| 46 | Dork in the Road (YouTube) | https://www.youtube.com/@DorkInTheRoad | 187K subs; 7.38% ER; ADV/dual-sport; dork@dorkintheroad.com |
| 47 | Delboy's Garage (YouTube) | https://www.youtube.com/@Moonfleet41 | 262K subs; ~18% ER; maintenance-focused; moonfleet10@yahoo.co.uk |
| 48 | The Bearded Mechanic (YouTube) | https://www.youtube.com/@TheBeardedMechanic | 637K subs; 5.52% ER; DIY teardowns |
| 49 | Bret Tkacs (YouTube) | https://www.youtube.com/@BretTkacs | 172K subs; 4.98% ER; ADV instruction |
| 50 | Big Rock Moto (YouTube) | https://www.youtube.com/@BigRockMoto | 488K subs; 4.94% ER; ADV reviews |
| 51 | MotoJitsu (YouTube) | https://www.youtube.com/@MotoJitsu | 598K subs; 5.44% ER; new rider focus; gregory.widmar@gmail.com |
| 52 | FortNine (YouTube) | https://www.youtube.com/@FortNine | 2.29M subs; 6.02% ER; media-commerce hybrid |
| 53 | Itchy Boots (YouTube) | https://www.youtube.com/@ItchyBoots | 3.25M subs; 10.26% ER; travel focus; low maintenance fit |
| 54 | VidIQ / youtubers.me channel stats | https://vidiq.com | Engagement rate and view data for influencer ranking |
| 55 | ADV Pulse: Big Rock Moto Feature | https://www.advpulse.com/adv-news/5-riders-who-turned-their-2-wheel-passion-into-a-full-time-job/ | Channel profile and growth context |
| 56 | Feedspot: 100 Motorcycle YouTube Channels 2026 | https://videos.feedspot.com/motorcycle_youtube_channels/ | Influencer discovery source |
| 57 | Riders Share Blog: 15 Motorcycle Influencers | https://www.riders-share.com/blog/article/15-motorcycle-influencers-you-should-be-following | Influencer discovery source |
