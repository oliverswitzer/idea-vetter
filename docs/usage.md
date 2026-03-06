# Usage Guide

## Quick Start

Open Claude Code in the project directory:

```bash
cd mvp-vetter
claude
```

Then describe your idea:

```
Vet this idea: a SaaS tool that helps freelance designers manage client feedback
and revision requests in one place, replacing scattered email threads and
Slack messages.
```

Claude will follow the Idea Vetter workflow automatically, using the project instructions in `.claude/CLAUDE.md`.

## Workflow Overview

The system works in phases:

1. **Frame** - Break the idea into structured components
2. **Research** - Gather evidence from multiple sources
3. **Synthesize** - Cluster and score findings
4. **Challenge** - Argue against the idea
5. **Recommend** - Propose a wedge and verdict

## Example Prompts

### Vet a raw idea
```
Vet this SaaS idea: [describe your idea]
```

### Analyze a specific market
```
Analyze the market for [category]. Who are the top players, what do users
complain about, and where are the gaps?
```

### Deep dive on competitors
```
Do a competitor analysis for [product category]. Include pricing, ratings,
review themes, and feature gaps.
```

### Generate a report
```
Take the research we've gathered and produce a full vetting report.
Save it to reports/.
```

### Export a report
```
Convert reports/2024-01-15-my-idea.md to PDF using Pandoc.
```

## Using Skills Directly

You can invoke skills by referencing them:

```
Use the idea-scoper skill to break down this idea: [idea]
```

```
Use the market-evidence-synthesizer skill to analyze these findings: [paste or reference data]
```

```
Use the report-composer skill to write the final report from our research.
```

## Using Subagents

For parallel research, ask Claude to delegate:

```
Launch the trend-researcher and app-store-analyst agents in parallel to
investigate [topic].
```

Or Claude will delegate automatically based on the workflow phase.

## Tips

- **Be specific**: "A tool for freelance designers to manage revisions" is better than "a project management tool"
- **Provide context**: If you know the target market, pricing range, or distribution channel, say so upfront
- **Challenge the output**: Ask follow-up questions like "What's the strongest argument against this?" or "Is there a narrower wedge?"
- **Iterate**: You can refine the idea and re-run specific phases without starting over
- **Save reports**: Always save final reports to `reports/` for version control
