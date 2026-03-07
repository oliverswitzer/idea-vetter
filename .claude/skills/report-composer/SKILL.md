---
name: report-composer
description: Assemble a polished, structured vetting report from synthesized evidence. Use when research and synthesis are complete and you need the final deliverable.
argument-hint: "[idea name or slug for filename]"
---

Compose the final vetting report for: $ARGUMENTS

Gather all available evidence (idea scope, evidence synthesis, trend data, app store data) from the current session and assemble the report.

## Step 1: Write Executive Summary
- 150 words max
- State the idea, the verdict, and the single most important finding
- Do not hedge excessively; take a position

## Step 2: State the Verdict
One of: **Proceed** / **Pivot** / **Niche Down** / **Kill**
With a 2-3 sentence justification.

## Step 3: Compile Idea Snapshot
Pull from the idea scope: user, job, trigger, outcome, key assumptions.

## Step 4: Assemble Demand and Trend Signals
Summarize search volume, trend direction, seasonality, related queries. Include data tables if available.

## Step 5: Map Competitor Landscape
Table format: name, positioning, pricing, monthly downloads (Sensor Tower), monthly revenue (Sensor Tower), strengths, weaknesses, notable gaps.

Include a "Revenue Landscape" summary below the table: which apps are making real money, what revenue tier the market sits in, and what that implies about willingness to pay. If Sensor Tower data is bucketed (e.g. `< $5k`), report the bucket and interpret it.

## Step 6: Present Pain Points
Use the scored clusters from the evidence synthesis. Include representative quotes with attribution.

## Step 7: Highlight Solution Gaps
List the most significant gaps with supporting evidence.

## Step 8: Describe Underserved Segments
For each segment: who they are, why they are underserved, size estimate if possible.

## Step 9: Present Money Signals
Evidence of willingness to pay, organized by signal type. This must include:
- Sensor Tower revenue estimates for top competitors (with source noted as Sensor Tower)
- IAP pricing tiers observed across competitor apps
- Any paid/subscription apps with meaningful download volume
- Pricing language signals from app store descriptions or reviews

## Step 10: List Communities and Channels
Where do target users gather? Forums, subreddits, Slack groups, newsletters, conferences.

## Step 11: Write MVP Recommendation
- Target segment
- Core feature set (3-5 features max)
- Pricing model suggestion
- First distribution channel
- Success metric for validation

## Step 12: Argue the Anti-Thesis
- 3-5 strongest reasons this idea could fail
- For each, state whether it is fatal or manageable

## Step 13: Produce Final Scorecard

| Dimension | Score | Notes |
|---|---|---|
| Problem severity | /10 | ... |
| Frequency | /10 | ... |
| Urgency | /10 | ... |
| Willingness to pay | /10 | ... |
| Competition pressure | /10 | ... |
| Accessibility of customer | /10 | ... |
| Defensibility potential | /10 | ... |
| Speed to MVP | /10 | ... |
| **Overall opportunity** | **/10** | ... |

## Step 14: Compile Sources Appendix
List all sources referenced in the report with URLs and access dates.

## Output Rules
- Save as `reports/YYYY-MM-DD-[slug].md`
- Keep under 3000 words
- Prefer tables over prose for comparisons
- Every factual claim must have a source in the appendix
