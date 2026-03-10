---
name: idea-vetter.market-evidence-synthesizer
description: Take raw research data (search results, forum posts, reviews, trend data, competitor info) and produce structured, scored analysis. Use after collecting evidence to cluster pain points, score them, map workarounds, and assess evidence quality.
argument-hint: "[idea name or context]"
---

Synthesize the collected research evidence for: $ARGUMENTS

Work through all gathered evidence (web searches, app store data, trend data, forum posts, reviews) and produce a structured analysis.

## Step 1: Cluster Pain Points
Group all observed complaints, frustrations, and unmet needs into themes. For each theme:
- Give it a descriptive name
- List 2-5 representative quotes or observations (with sources)
- Note the frequency across sources

## Step 2: Score Pain Points
Rate each pain point cluster:

| Dimension | Scale | Meaning |
|---|---|---|
| Frequency | 1-10 | How often this comes up across sources |
| Intensity | 1-10 | How strongly people express frustration |
| Urgency | 1-10 | How time-sensitive the need is |
| Monetization signal | 1-10 | Evidence people would pay to fix this |

## Step 3: Map Workarounds
For each pain point, identify what people currently do instead:
- Manual processes (spreadsheets, email, paper)
- Competitor products (name them, note limitations)
- Cobbled-together tool stacks
- Simply tolerating the problem

Note why each workaround fails or frustrates.

## Step 4: Identify Solution Gaps
Where do current solutions fall short? Look for:
- Features mentioned but not available
- Segments complaining they are ignored
- Pricing gaps (too expensive or no free tier)
- Integration gaps
- UX complaints

## Step 5: Identify Underserved Segments
Which user groups are poorly served and why?
- Too small for enterprise tools
- Too technical for consumer tools
- In a niche vertical
- In a geography with fewer options

## Step 6: Extract Money Signals
Compile evidence of willingness to pay:
- Active paid competitors with visible pricing
- Users asking "is there a paid version?"
- Premium tiers, upsells, enterprise plans
- Job postings for roles that indicate budget
- Agency/consultant activity in the space

## Step 7: Assess Evidence Quality
For each major finding, rate confidence:
- **Strong**: Multiple independent sources, recent, specific
- **Moderate**: A few sources, somewhat recent, plausible
- **Weak**: Single source, old, vague, or potentially biased

## Output Format

```markdown
## Evidence Synthesis: [Idea Name]

### Pain Point Clusters
| # | Theme | Frequency | Intensity | Urgency | Money Signal | Confidence |
|---|---|---|---|---|---|---|
| 1 | ... | /10 | /10 | /10 | /10 | Strong/Moderate/Weak |

#### [Theme 1 Name]
- Evidence: ...
- Sources: ...

### Current Workarounds
| Workaround | Why It Fails |
|---|---|
| ... | ... |

### Solution Gaps
1. ...
2. ...

### Underserved Segments
1. **[Segment]**: [Why underserved]

### Money Signals
- ...

### Evidence Quality Summary
- Strong evidence for: ...
- Weak evidence for: ...
- Missing evidence on: ...
```
