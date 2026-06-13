---
description: Generate an AI briefing for a specific SEC filing — materiality, direction, plain-English what-happened / what-it-means / what-to-watch.
argument-hint: <accession | ticker form date>
---

# Filing Briefing

You are generating a human-readable briefing for a specific SEC filing.

## Input
A filing accession (e.g. `0000320193-25-000079`) or a (ticker, form, date): $ARGUMENTS

## Workflow
1. **Resolve the filing** — if given an accession, use it; else `search_filings` to find the matching accession.
2. **Get the briefing** — call `get_filing_briefing` / `GET /v1/filings/{accession}/briefing`. It returns `materiality` (1–3), `direction` (bullish/bearish/neutral/ambiguous), and an AI `summary` / `what_it_means` / `what_to_watch` (best-effort), plus `basis` (cited source + confidence).
3. **Enrich if useful** — for an 8-K use `get_8k_events`; for a 10-K/10-Q use `extract_filing_section` (item `7` MD&A, `1A` risk factors); for a Form 4 use `get_insider_filing`.
4. **Present**:
   ```
   ## {Company} — {Form} — {Filed date}
   Materiality: {1-3}  |  Direction: {direction}
   ### What happened
   ### Why it matters
   ### What to watch
   ### Source
   {accession} · {EDGAR url}
   ```

## Notes
- Plain English; flag any caveats. Always cite the source filing.
