# Vetting Report: Partner Knowledge App

**Date:** 2026-03-06
**Idea:** A voice-narration app that builds a GraphRAG knowledge graph about your romantic partner, then serves personalized date recommendations, gift ideas, and important date reminders. Monetized via subscription + affiliate marketing.

---

## 1. Executive Summary

The problem is real and well-documented: 82% of people have forgotten an anniversary, 88% struggle with gift ideas, and partners are the #1 gift recipient. People already manually track partner details in Notes apps — a behavior that went viral on TikTok with overwhelmingly positive reception. The couples app market ($2B, growing 12.5% CAGR) and personalized gifts market ($31B, growing 9% CAGR) are both expanding. Critically, **no existing app bridges "know your partner" with "act on it"** — couples apps collect data that goes nowhere, and AI gift tools start from zero every time. Lovewick's manual "Forget-me-nots" is the closest feature but has no AI, no voice input, and generates no recommendations. The core risk is seasonal engagement: gift/date help is needed 4-5 times per year, but the knowledge graph requires year-round input to be valuable. **Proceed with a niche-down MVP targeting men 25-45, leading with voice capture and gift recommendations before Valentine's Day or Christmas.**

---

## 2. Verdict: PROCEED (with niche-down)

The gap between "knowing your partner" and "acting on that knowledge" is validated, unoccupied, and monetizable. No well-funded competitor has executed on this combination. The key risk — year-round engagement — can be tested cheaply before building the full GraphRAG system. Start narrow: voice-captured partner profile + AI gift recommendations for the next gifting occasion.

---

## 3. Idea Snapshot


| Component        | Description                                                                                                                                                                                       |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Target user      | Men 25-45 in committed relationships who want to be more thoughtful but lack a system                                                                                                             |
| Job to be done   | Effortlessly remember everything about my partner and always have personalized gift/date ideas ready                                                                                              |
| Trigger moment   | Forgetting an anniversary, blanking on gift ideas before a birthday/holiday, partner expressing disappointment                                                                                    |
| Expected outcome | Never miss an important date, always have personalized recommendations, feel confident as a thoughtful partner                                                                                    |
| Key assumptions  | Voice narration is a natural input method; users will engage between holidays; AI recommendations are meaningfully better than Google; users will pay $5-10/mo; the concept doesn't feel "creepy" |


---

## 4. Demand and Trend Signals

### Market Size


| Segment                          | Value                 | Growth                            | Source                                                                                                                            |
| -------------------------------- | --------------------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Couples app market               | $2B (2024)            | 12.5% CAGR to $5.77B by 2033      | [Business Research Insights](https://www.businessresearchinsights.com/market-reports/relationship-apps-for-couples-market-117629) |
| Personalized gifts market        | $31-34B (2025)        | 9% CAGR to $43-65B by early 2030s | [Verified Market Research](https://www.verifiedmarketresearch.com/product/personalized-gifts-market/)                             |
| US date + gift spending          | ~$80B/year            | —                                 | Lovewick estimate                                                                                                                 |
| Valentine's Day total spend      | $27.5B (2025, record) | Growing YoY                       | [NRF via Accio](https://www.accio.com/business/valentinesdaytrend2025)                                                            |
| Average annual gift spend/person | $1,000-1,200          | —                                 | [NCH Stats](https://nchstats.com/americans-spend-on-gifts/)                                                                       |


### Search Demand & Seasonality


| Keyword                             | Est. Monthly Volume | Trend                    |
| ----------------------------------- | ------------------- | ------------------------ |
| "gifts for men"                     | ~90,500             | Stable + seasonal spikes |
| "gifts for her" (Etsy)              | >2,000,000          | High volume              |
| "personalized gifts for girlfriend" | Surged 40%+ YoY     | Growing                  |
| "gift ideas for wife/husband"       | Tens of thousands   | Stable, seasonal peaks   |


**Seasonality pattern:** Demand is extremely concentrated — Christmas (largest), Valentine's Day (2nd), Mother's/Father's Day. Searches spike 2-3x during peaks and drop to near-zero between them. This creates a core product design challenge: the app needs engagement between holidays to build the knowledge that makes holiday moments valuable.

Source: [Google Holiday 100](https://blog.google/products-and-platforms/products/shopping-payments/holiday-100-2025/), [Cedarwood Digital](https://cedarwood.digital/blog/valentines-day-search-data/), [AdTargeting.io](https://adtargeting.io/industry/gift-ideas-keywords)

---

## 5. Competitor Landscape

### Couples Apps (with Sensor Tower Revenue Estimates)


| App          | Rating | Reviews | Price        | Est. MRR        | Est. Downloads/mo | Partner Profile?     | Gift Recs? |
| ------------ | ------ | ------- | ------------ | --------------- | ----------------- | -------------------- | ---------- |
| Paired       | 4.7    | 194K    | $14.99/mo    | **~$400K** (US) | ~110K             | No                   | No         |
| Evergreen    | 4.8    | 53K     | $9.99-69.99  | **~$70-90K**    | ~20K              | No                   | No         |
| Between      | 4.8    | 21K     | $2.99/mo     | ~$90K (stale)   | ~80K (declining)  | No                   | No         |
| Couple Joy   | 4.9    | 29.6K   | $12.99-39.99 | Not surfaced    | ~280K (Android)   | No                   | No         |
| Cozy Couples | 4.8    | 35.3K   | $4.99-39.99  | ~$10-70K        | ~9-70K            | No                   | No         |
| Lovewick     | 4.8    | 1.9K    | $9.99/mo     | Not surfaced    | Not surfaced      | **Partial** (manual) | No         |
| Flamme       | 4.3    | 2.9K    | Freemium     | Not surfaced    | ~8K               | No                   | No         |
| Couply       | 4.6    | 1.5K    | ~$69.99/yr   | Not surfaced    | ~5K (declining)   | No                   | No         |


Sources: [Sensor Tower](https://app.sensortower.com/), [AppstoreSpy](https://appstorespy.com/), [Adapty](https://adapty.io/), [AppBrain](https://www.appbrain.com/)

**Key revenue insight:** Paired dominates at ~~$400K/mo US (~~$1.2M global). But Evergreen is the most interesting signal — only ~20K downloads/month yet $70-90K MRR, a $3.50-4.50 revenue-per-download ratio. This proves a well-positioned relationship app can extract meaningful revenue from a modest user base. You don't need Paired's scale to build a real business.

**Key feature insight:** Every couples app stops at "learn about each other." None convert knowledge into actionable gift or date recommendations. Users explicitly request this in reviews.

### AI Gift Tools


| Tool                                      | Persistent Profile?                | Learns Over Time? | Model             |
| ----------------------------------------- | ---------------------------------- | ----------------- | ----------------- |
| GyftPro                                   | No                                 | No                | Free/affiliate    |
| Giftly (web)                              | **Yes** (social media + purchases) | **Yes** (ML)      | Unknown           |
| GiftStar AI, Giftruly, DreamGift, Outdone | No                                 | No                | Free/affiliate    |
| Giftful                                   | No (wishlist)                      | No                | Free              |
| Target AI Gift Finder                     | No                                 | No                | Integrated retail |


**Key finding:** All are stateless one-shot tools except Giftly (web-only, not partner-specific). No tool combines persistent partner knowledge with gift recommendations.

### Closest Competitor: Lovewick

Lovewick is the only app with a partner detail storage feature ("Forget-me-nots"). It also has 750+ date ideas. However:

- Forget-me-nots is **manual text entry** — no voice, no AI extraction, no knowledge graph
- Date ideas use **generic filters** (cost, time) — not personalized to partner preferences
- **No gift recommendations** generated from stored data
- Early stage ($1M pre-seed, 300K users) — could add AI features but hasn't yet

Source: [Lovewick](https://lovewick.com/), [App Store](https://apps.apple.com/us/app/lovewick-relationship-tracker/id1516199115)

---

## 6. Pain Points (Scored)


| #   | Theme                                      | Freq | Intensity | Urgency | Money Signal | Confidence |
| --- | ------------------------------------------ | ---- | --------- | ------- | ------------ | ---------- |
| 1   | Forgetting important dates                 | 9    | 8         | 9       | 7            | Strong     |
| 2   | Gift selection paralysis                   | 9    | 7         | 8       | 8            | Strong     |
| 3   | Failing to retain partner details          | 7    | 6         | 4       | 5            | Moderate   |
| 4   | Apps collect data but do nothing with it   | 6    | 7         | 5       | 6            | Moderate   |
| 5   | Generic recs that don't know the recipient | 7    | 6         | 7       | 7            | Moderate   |
| 6   | Gift fatigue and cost pressure             | 6    | 5         | 6       | 4            | Strong     |


**Representative evidence:**

- "82% of people have forgotten their anniversary. 68% said they would break up if their partner forgot." — [Dating.com/PRNewswire](https://www.prnewswire.com/news-releases/forgetting-your-anniversary-could-spell-doom-for-your-relationship-datingcom-survey-reveals-301831596.html)
- "88% of people sometimes struggle to come up with gift ideas." — [GiftAFeeling Statistics 2025](https://www.giftafeeling.com/pages/gift-giving-statistics-2025)
- "No one has mastered the art of mind-reading, yet people feel let down because their spouse couldn't read their mind." — MetaFilter forum
- "When I unlocked his phone it opened to a note that was just a list of everything I've ever mentioned that I liked." — Reddit (viral, universally praised)

---

## 7. Solution Gaps

1. **Know-to-Act Bridge:** No app connects partner knowledge to actionable recommendations. Every couples app stops at discovery; every gift app starts from scratch.
2. **Persistent AI Partner Profile:** Lovewick's Forget-me-nots is the only attempt — it's a manual notes list with no intelligence layer.
3. **Voice-First Relationship Input:** Zero apps use voice narration for partner knowledge capture. Voice journaling apps exist but none are relationship-focused.
4. **Contextual Recommendations:** No app generates "Based on Sarah's love of sushi and quality time love language, here are 3 date ideas for Saturday."
5. **Temporal Awareness:** No app tracks how preferences evolve. A partner who loved hiking 2 years ago may now prefer cooking classes.

---

## 8. Underserved Segments


| Segment                          | Why Underserved                                                                                                                                                                | Size Signal                                 |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------- |
| **Men 25-45 in relationships**   | 82% of anniversary forgetters are male. Couples apps skew toward female-initiated communication/therapy. No app targets "I want to be better at this but don't have a system." | ~50M men in US relationships                |
| **Long-term couples (5+ years)** | Quiz-based apps run out of content. These couples need gift freshness and novelty, not "getting to know each other" questions.                                                 | Majority of 130M US adults in relationships |
| **Neurodivergent partners**      | Acute need for structured social memory. Monica CRM received explicit praise from users with Asperger's and Alzheimer's.                                                       | Small but intensely loyal                   |
| **Gift-anxious partners**        | 88% struggle with gift ideas, 48% report gift fatigue. Would pay to offload cognitive burden.                                                                                  | Broadly overlaps with primary target        |


---

## 9. Money Signals


| Signal                                 | Evidence                                                                                                                                                                                                                                              |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Sensor Tower: real MRR in category** | Paired ~$400K/mo (US), Evergreen ~$70-90K/mo, Between ~$90K/mo (stale), Cozy Couples ~$10-70K/mo. The category generates real subscription revenue.                                                                                                   |
| **High revenue-per-download possible** | Evergreen earns $70-90K/mo from only ~20K downloads/mo ($3.50-4.50/download). Proves you don't need massive scale — retention and perceived value matter more.                                                                                        |
| **Subscription pricing validated**     | $9-15/mo or $30-70/yr is the proven range. Paired user: "It may seem like a lot to spend $70 for the year but man it's so worth it. Just look at it like a date night."                                                                               |
| **Affiliate opportunity**              | Gift affiliate programs: 10-40% commission. Experience/date booking affiliates available. Emotional buying drives higher conversion.                                                                                                                  |
| **Massive spending on gifts**          | Average $1,000-1,200/person/year on gifts. Partners are #1 recipient (60%+).                                                                                                                                                                          |
| **Counter-signal**                     | Gift-specific subscription apps struggle (GiftPal at $99.99/yr has 3 ratings). AI gift tools are mostly free. Subscription must be justified by relationship value, not gift value alone. Gift apps (Giftful) have adoption but unclear monetization. |


---

## 10. Communities and Channels


| Channel                                             | Relevance                                                 | Reach                     |
| --------------------------------------------------- | --------------------------------------------------------- | ------------------------- |
| r/AskMen, r/relationship_advice                     | Gift-giving pain discussed frequently                     | 10M+ combined subscribers |
| TikTok (#rulesfordating, #partnernoteslist)         | Viral trend of men keeping partner notes                  | 771K+ views on hashtag    |
| Men's lifestyle newsletters/podcasts                | Thoughtful partner content resonates                      | Varies                    |
| Valentine's Day / Christmas gift guide SEO          | Seasonal but massive intent                               | Millions of searches      |
| Couples therapy / relationship coaching communities | Adjacent audience, referral potential                     | Growing                   |
| Product Hunt / Hacker News                          | Tech-forward early adopters, Monica CRM got traction here | Engaged niche             |


---

## 11. MVP Recommendation

**Target segment:** Men 25-40 in relationships of 1+ year, self-identified as "bad at gifts/remembering details."

**Core feature set (v1):**

1. **Voice capture** — Talk about your partner anytime; AI transcribes and extracts entities (preferences, dates, sizes, interests) into a structured profile
2. **Partner profile view** — Browse and curate the accumulated knowledge about your partner, organized by category
3. **Smart reminders** — Important dates with 2-week advance notice + suggested actions
4. **AI gift recommendations** — Personalized suggestions based on the profile, with affiliate purchase links
5. **Date idea generator** — Contextual date suggestions based on partner preferences + location + budget

**Pricing:** Freemium. Free tier: voice capture + profile (limited entries). Premium ($7.99/mo or $49.99/yr): unlimited entries, AI gift/date recommendations, smart reminders, affiliate shopping.

**First distribution channel:** TikTok content marketing leveraging the existing "partner notes" trend. Demo videos showing voice capture to smart gift suggestion pipeline. Target pre-Valentine's Day or pre-Christmas launch for maximum seasonal demand.

**Validation metric:** 500 users with 3+ voice entries AND 1+ gift recommendation click-through within 60 days of launch. This tests both the input habit (voice capture retention) and the output value (recommendation quality).

**What to skip in v1:** GraphRAG (use simple structured storage + LLM queries), Pinterest/Instagram ingestion (API risk + complexity), Florence 2 image model (premature optimization). Validate the core loop first.

---

## 12. Risks and Anti-Thesis


| Risk                                                                                                                                                                                                                    | Severity | Fatal?      | Mitigation                                                                                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Seasonal engagement gap** — Users need gift help 4-5x/year but the knowledge graph needs year-round input. Without a retention hook between holidays, churn will be extreme.                                          | High     | Potentially | Add weekly "partner check-in" prompts, relationship milestone tracking, "things to try this weekend" nudges. Test retention before building complex features.                                                                    |
| **Creepiness perception** — The same behavior (tracking partner details) is "romantic" on TikTok but "creepy" when framed as a database. One viral negative take could damage the brand.                                | Medium   | Manageable  | Frame as "love journal" not "partner CRM." Emphasize privacy (on-device storage, no cloud). Let users share the concept with partners openly.                                                                                    |
| **Lovewick or Paired adds AI** — Both have existing user bases (300K and 8M). Either could ship an AI gift recommendation layer in months.                                                                              | Medium   | Manageable  | Move fast. The knowledge graph + voice input create switching costs that grow over time. First-mover advantage on accumulated data matters.                                                                                      |
| **Gift recommendations aren't good enough** — If AI suggestions feel generic despite the knowledge graph, the core value proposition collapses. Users just go back to Google.                                           | High     | Potentially | Invest heavily in recommendation quality. Use the knowledge graph to generate highly specific suggestions ("that exact pottery studio she mentioned in March" not "a pottery class"). Curate affiliate partnerships for quality. |
| **Small TAM for dedicated app** — People who will download, maintain, and pay for a dedicated "partner knowledge" app may be a tiny fraction of the 88% who struggle with gifts. Most will stick with Notes or ChatGPT. | Medium   | Manageable  | Start with the most motivated segment (men who've already been burned by forgetting). Consider whether this should be a feature inside an existing app rather than standalone.                                                   |


---

## 13. Final Scorecard


| Dimension                 | Score    | Notes                                                                                                                                                                       |
| ------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Problem severity          | 7/10     | Real and emotionally charged, but intermittent — acute 4-5x/year                                                                                                            |
| Frequency                 | 6/10     | Seasonal spikes with unclear year-round engagement                                                                                                                          |
| Urgency                   | 7/10     | High before holidays/anniversaries, low otherwise                                                                                                                           |
| Willingness to pay        | 7/10     | Sensor Tower confirms ~$400K/mo (Paired), ~$70-90K/mo (Evergreen) at $9-15/mo. Evergreen proves high revenue possible from modest downloads. Gift-only apps still struggle. |
| Competition pressure      | 8/10     | No direct competitor. Lovewick closest but early/manual                                                                                                                     |
| Accessibility of customer | 7/10     | Men 25-45 reachable via TikTok, Reddit, seasonal SEO                                                                                                                        |
| Defensibility potential   | 5/10     | Knowledge graph creates switching costs; but no network effects and incumbents could add features                                                                           |
| Speed to MVP              | 7/10     | Voice transcription + LLM + basic profile is fast; skip GraphRAG for v1                                                                                                     |
| **Overall opportunity**   | **7/10** | **Real gap, growing market, clear wedge. Proceed — but validate retention before building complexity.**                                                                     |


---

## 14. Sources Appendix


| #   | Source                                          | URL                                                                                                                                                                                                                                                                                                                          |
| --- | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Dating.com Anniversary Survey                   | [https://www.prnewswire.com/news-releases/forgetting-your-anniversary-could-spell-doom-for-your-relationship-datingcom-survey-reveals-301831596.html](https://www.prnewswire.com/news-releases/forgetting-your-anniversary-could-spell-doom-for-your-relationship-datingcom-survey-reveals-301831596.html)                   |
| 2   | GiftAFeeling Statistics 2025                    | [https://www.giftafeeling.com/pages/gift-giving-statistics-2025](https://www.giftafeeling.com/pages/gift-giving-statistics-2025)                                                                                                                                                                                             |
| 3   | GiftRabbit Statistics 2026                      | [https://giftrabbit.com/gift-giving-statistics-and-facts/](https://giftrabbit.com/gift-giving-statistics-and-facts/)                                                                                                                                                                                                         |
| 4   | NCH Stats Gift Spending                         | [https://nchstats.com/americans-spend-on-gifts/](https://nchstats.com/americans-spend-on-gifts/)                                                                                                                                                                                                                             |
| 5   | Google Holiday 100 2025                         | [https://blog.google/products-and-platforms/products/shopping-payments/holiday-100-2025/](https://blog.google/products-and-platforms/products/shopping-payments/holiday-100-2025/)                                                                                                                                           |
| 6   | Accio Valentine's Day Trends                    | [https://www.accio.com/business/valentinesdaytrend2025](https://www.accio.com/business/valentinesdaytrend2025)                                                                                                                                                                                                               |
| 7   | Cedarwood Digital Valentine's Data              | [https://cedarwood.digital/blog/valentines-day-search-data/](https://cedarwood.digital/blog/valentines-day-search-data/)                                                                                                                                                                                                     |
| 8   | SEMrush Valentine's Day Data                    | [https://www.semrush.com/news/380949-valentines-day-a-data-driven-love-story-of-trends-searches-and-online-dating/](https://www.semrush.com/news/380949-valentines-day-a-data-driven-love-story-of-trends-searches-and-online-dating/)                                                                                       |
| 9   | Business Research Insights - Couples App Market | [https://www.businessresearchinsights.com/market-reports/relationship-apps-for-couples-market-117629](https://www.businessresearchinsights.com/market-reports/relationship-apps-for-couples-market-117629)                                                                                                                   |
| 10  | Verified Market Research - Personalized Gifts   | [https://www.verifiedmarketresearch.com/product/personalized-gifts-market/](https://www.verifiedmarketresearch.com/product/personalized-gifts-market/)                                                                                                                                                                       |
| 11  | Paired iOS App Store                            | [https://apps.apple.com/us/app/paired-couples-relationship/id1469609343](https://apps.apple.com/us/app/paired-couples-relationship/id1469609343)                                                                                                                                                                             |
| 12  | Lovewick iOS App Store                          | [https://apps.apple.com/us/app/lovewick-relationship-tracker/id1516199115](https://apps.apple.com/us/app/lovewick-relationship-tracker/id1516199115)                                                                                                                                                                         |
| 13  | Lovewick Website                                | [https://lovewick.com/](https://lovewick.com/)                                                                                                                                                                                                                                                                               |
| 14  | Between iOS App Store                           | [https://apps.apple.com/us/app/between-the-app-couples-love/id458035189](https://apps.apple.com/us/app/between-the-app-couples-love/id458035189)                                                                                                                                                                             |
| 15  | Monica CRM GitHub                               | [https://github.com/monicahq/monica](https://github.com/monicahq/monica)                                                                                                                                                                                                                                                     |
| 16  | Monica on Hacker News                           | [https://news.ycombinator.com/item?id=25270001](https://news.ycombinator.com/item?id=25270001)                                                                                                                                                                                                                               |
| 17  | GyftPro Launch PR                               | [https://www.morningstar.com/news/pr-newswire/20251202ph36269/gyftpro-launches-the-first-social-gifting-app-that-uses-ai-to-bring-meaning-back-to-gift-giving](https://www.morningstar.com/news/pr-newswire/20251202ph36269/gyftpro-launches-the-first-social-gifting-app-that-uses-ai-to-bring-meaning-back-to-gift-giving) |
| 18  | Giftly AI Engine Blog                           | [https://giftly.app/blog/gift-recommendations-made-easy-a-deep-dive-into-giftly-s-ai-engine](https://giftly.app/blog/gift-recommendations-made-easy-a-deep-dive-into-giftly-s-ai-engine)                                                                                                                                     |
| 19  | TikTok Partner Notes Trend                      | [https://dallassinglemom.com/this-viral-trend-reveals-the-surprising-notes-many-men-keep-about-their-partners/](https://dallassinglemom.com/this-viral-trend-reveals-the-surprising-notes-many-men-keep-about-their-partners/)                                                                                               |
| 20  | Reddit Gift List Story                          | [https://www.someecards.com/lifestyle/gifts/man-asks-for-help-getting-a-gift-for-his-thoughtful-wife-reddit-delivers-updated/](https://www.someecards.com/lifestyle/gifts/man-asks-for-help-getting-a-gift-for-his-thoughtful-wife-reddit-delivers-updated/)                                                                 |
| 21  | Obsidian Forum - Relationship Notes             | [https://forum.obsidian.md/t/making-and-maintaining-notes-on-friends-relationships/82918](https://forum.obsidian.md/t/making-and-maintaining-notes-on-friends-relationships/82918)                                                                                                                                           |
| 22  | Psychology Today - Gifts and Marriage           | [https://www.psychologytoday.com/us/blog/contemplating-divorce/201712/what-gifts-your-spouse-say-about-your-marriage](https://www.psychologytoday.com/us/blog/contemplating-divorce/201712/what-gifts-your-spouse-say-about-your-marriage)                                                                                   |
| 23  | Paired Seed Round (TechCrunch)                  | [https://techcrunch.com/2021/05/27/paired-pulls-in-3-6m-to-encourage-more-couples-to-get-cosy-with-app-based-relationship-care/](https://techcrunch.com/2021/05/27/paired-pulls-in-3-6m-to-encourage-more-couples-to-get-cosy-with-app-based-relationship-care/)                                                             |
| 24  | Lovewick Pre-Seed (BusinessWire)                | [https://www.businesswire.com/news/home/20220214005133/en/Lovewick-An-App-to-Help-Couples-Stay-in-Love-Beyond-the-Match-Raises-1M-Pre-seed](https://www.businesswire.com/news/home/20220214005133/en/Lovewick-An-App-to-Help-Couples-Stay-in-Love-Beyond-the-Match-Raises-1M-Pre-seed)                                       |
| 25  | Sifted - Startups Fixing Love                   | [https://sifted.eu/articles/startups-fixing-love-digitally](https://sifted.eu/articles/startups-fixing-love-digitally)                                                                                                                                                                                                       |
| 26  | AdTargeting Gift Keywords                       | [https://adtargeting.io/industry/gift-ideas-keywords](https://adtargeting.io/industry/gift-ideas-keywords)                                                                                                                                                                                                                   |
| 27  | Bastian Moritz - Personal CRM                   | [https://www.bastianmoritz.com/writing/why-a-personal-crm-is-personal-in-every-sense/](https://www.bastianmoritz.com/writing/why-a-personal-crm-is-personal-in-every-sense/)                                                                                                                                                 |
| 28  | Business of Apps - Dating App Market            | [https://www.businessofapps.com/data/dating-app-market/](https://www.businessofapps.com/data/dating-app-market/)                                                                                                                                                                                                             |
| 29  | Futurepedia - AI Gift Tools                     | [https://www.futurepedia.io/ai-tools/gift-ideas](https://www.futurepedia.io/ai-tools/gift-ideas)                                                                                                                                                                                                                             |
| 30  | CNBC Gift Spending                              | [https://www.cnbc.com/2025/11/20/how-much-americans-say-they-spend-on-gifts-for-weddings-birthdays.html](https://www.cnbc.com/2025/11/20/how-much-americans-say-they-spend-on-gifts-for-weddings-birthdays.html)                                                                                                             |
| 31  | Paired on Sensor Tower (iOS)                    | [https://app.sensortower.com/overview/1469609343?country=us](https://app.sensortower.com/overview/1469609343?country=us)                                                                                                                                                                                                     |
| 32  | Paired on Sensor Tower (Android)                | [https://app.sensortower.com/overview/com.getpaired.app?country=us](https://app.sensortower.com/overview/com.getpaired.app?country=us)                                                                                                                                                                                       |
| 33  | Evergreen on Sensor Tower                       | [https://app.sensortower.com/overview/1573360122?country=US](https://app.sensortower.com/overview/1573360122?country=US)                                                                                                                                                                                                     |
| 34  | Between on Sensor Tower (iOS)                   | [https://app.sensortower.com/ios/us/vcnc/app/between-the-app-couples-love/458035189](https://app.sensortower.com/ios/us/vcnc/app/between-the-app-couples-love/458035189)                                                                                                                                                     |
| 35  | Paired on AppstoreSpy                           | [https://appstorespy.com/android-google-play/com.getpaired.app-trends-revenue-statistics-downloads-ratings](https://appstorespy.com/android-google-play/com.getpaired.app-trends-revenue-statistics-downloads-ratings)                                                                                                       |
| 36  | Cozy Couples paywall (Adapty)                   | [https://adapty.io/paywall-library/cozy/](https://adapty.io/paywall-library/cozy/)                                                                                                                                                                                                                                           |
| 37  | Couply funding (BetaKit)                        | [https://betakit.com/former-wattpad-employees-close-300000-to-build-relationship-improvement-app-couply/](https://betakit.com/former-wattpad-employees-close-300000-to-build-relationship-improvement-app-couply/)                                                                                                           |


