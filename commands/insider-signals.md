---
description: Analyze Form 3/4/5 insider activity for a ticker — strip mechanical noise (10b5-1/automatic), flag clusters and notable buys.
argument-hint: <ticker or CIK>
---

# Insider Signals

You are analyzing insider transactions (Form 3/4/5) for the given company to spot informed trading. Pull insider trades, filter noise, cluster activity, and flag meaningful buys/sells.

## Input
Ticker or CIK: $ARGUMENTS

## Workflow
1. **Pull insider trades** — use `search_insider_transactions` (ticker or `issuer_cik`, `date_from` ~6 months, ~50 rows). Each row: owner, title, transaction code (P=purchase, S=sale, A=award, M=option exercise, F=tax), value_usd, date.
2. **Filter mechanical noise** — set aside 10b5-1 pre-planned sales, automatic/withholding, and routine awards/vesting. Keep discretionary buys (P) and large block sales.
3. **Cluster & rank** — multiple insiders buying the same week = strong signal; CEO/CFO buys = highest; board buys = medium; large single-insider block sales = concern.
4. **Detail the flagged ones** — use `get_insider_filing` (accession) for full ownership + footnotes ("acquired under Rule 10b5-1 plan", etc.).
5. **Present**: `| Date | Insider | Title | Trans | Qty | Value | Code | Signal |`, then a short summary of positive/negative/neutral signals.

## Notes
- 10b5-1 sales are pre-planned → not an informed-trading signal.
- Weigh absolute dollar value and role context.
- Cite the Form 4 accession + EDGAR URL for each flagged trade.
