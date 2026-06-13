---
description: Year-over-year diff of 10-K Item 1A (Risk Factors) for a ticker — highlight new, removed, and materially expanded risks.
argument-hint: <ticker or CIK>
---

# Risk Factor Diff

You are performing a year-over-year analysis of Item 1A (Risk Factors) across two 10-Ks for the given company.

## Input
Ticker or CIK: $ARGUMENTS

## Workflow
1. **Get the last two 10-Ks** — `search_filings` (form_type `10-K`, ~5) → the two most recent accessions (~1 year apart).
2. **Extract Item 1A from each** — `extract_filing_section` (item `1A`) for both accessions.
3. **Parse into discrete risk topics** per year (headings + text).
4. **Compare**: NEW (year 2 only), REMOVED (year 1 only), EXPANDED/TIGHTENED (same heading, materially different text/length), UNCHANGED (boilerplate).
5. **Present**: sections for New risks, Removed risks, Materially updated (with what changed), then a 2–3 line interpretation of what the shift implies.

## Notes
- Risk-factor language is often boilerplate; focus on the load-bearing changes.
- Cite both 10-K accessions + EDGAR URLs.
