---
description: Track quarter-over-quarter 13F institutional holdings changes for a manager or a stock — entries, exits, and major adjustments.
argument-hint: <manager name | ticker/issuer>
---

# 13F Tracker

You are analyzing 13F institutional holdings to track quarter-over-quarter changes for a manager or a stock.

## Input
A fund manager name (e.g. "Berkshire Hathaway") or a ticker/issuer: $ARGUMENTS

## Workflow
### If a manager
1. **Find the manager** — `search_13f_managers` (name substring) → manager, AUM, latest filing.
2. **Get holdings across the two most recent quarters** — `search_13f_holdings` (manager, paginate to 100+). Per holding: issuer, CUSIP, qty, value.
3. **Diff quarters** — table `| Stock | Prev Qty/Value | Curr Qty/Value | Change | Signal |`. Flag: INCREASE (>20%), EXIT (>80% cut), NEW position.

### If a stock
1. **Find institutional holders** — `search_13f_holdings` (issuer name or cusip).
2. **Rank top holders** and show position changes across quarters.

## Notes
- 13F is quarterly (filed ~45 days after quarter end); it's a snapshot, not intraday.
- Small positions (<$100K) may be omitted.
- Cite the 13F-HR accession(s).
