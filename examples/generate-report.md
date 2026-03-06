# Example: Generate a Report from Evidence

## Context

Use this after you've already done research (either in the same session or by providing findings).

## Prompt (with prior research in session)

```
We've gathered enough evidence. Use the report-composer skill to write the full
vetting report. Save it to reports/.
```

## Prompt (with provided findings)

```
Here are my research findings for an AI-powered invoice processing tool for
small accounting firms:

Competitors: Dext (formerly Receipt Bank), Hubdoc, AutoEntry, Docyt
- Dext: $30/month, 4.1 stars, complaints about OCR accuracy and price increases
- Hubdoc: Free with Xero, limited standalone, 3.8 stars
- AutoEntry: $24/month, 4.3 stars, praised for accuracy, limited integrations

Pain points from r/accounting and r/bookkeeping:
- Manual data entry is the #1 time sink
- OCR tools misread handwritten invoices
- Integration with niche accounting software is poor
- Pricing scales badly for firms with many clients

Google Trends: "invoice automation" up 40% over 2 years
App store: Limited quality options on mobile

Use the report-composer skill to turn this into a full vetting report.
```

## What to Expect

The report-writer agent will:

1. Structure findings into the 14-section report format
2. Apply the scoring rubric based on evidence
3. Write a clear executive summary and verdict
4. Include all sources
5. Save to `reports/YYYY-MM-DD-ai-invoice-tool.md`

## Follow-up Prompts

```
Export the report to PDF.
```

```
The competition pressure score seems too low. Dext just raised $100M.
Adjust the analysis.
```
