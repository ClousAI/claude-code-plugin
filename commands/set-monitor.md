---
description: Create a real-time Clous monitor on a ticker, CIK, form, or event type — with materiality floor, event signals, and optional webhook delivery.
argument-hint: <what to watch, e.g. "NVDA high-materiality 8-Ks to https://...">
---

# Set Monitor

You are helping the user create a Clous monitor that watches for SEC events and optionally delivers matches to a webhook.

## Input
A natural-language watch request: $ARGUMENTS

## Workflow
1. **Clarify scope** — map to a target: `target_type` ∈ ticker | cik | company | form | event_type, and `target_value`. Optional `signals` (event-type slugs), `min_materiality` (1–3), `cadence` (1h|6h|1d|7d), `metadata` (echoed into the webhook for routing).
2. **Register a webhook (if requested)** — `create_webhook_endpoint` with the user's HTTPS URL → `endpoint_id`.
3. **Create the monitor** — `create_monitor` with name, target_type, target_value, signals, min_materiality, cadence, metadata, trigger_on_create, webhook_endpoint_id.
4. **Confirm** — echo back what it watches, materiality floor, cadence, webhook, and status (active). Mention the monitor id and that they can pause/update/delete it.

## Event taxonomy (signals)
`sec.8k.*` (executive_change, auditor_change, bankruptcy_or_receivership, results_of_operations, cybersecurity_incident, delisting_notice, material_agreement) · `sec.form4.insider_buy|insider_sell` · `sec.formd.new_offering` · `sec.s1.new_registration` · `sec.13f.position_increased|decreased` · `sec.proxy.board_changed`. See docs.clous.ai/docs/api/events.

## Notes
- Webhook payloads are HMAC-signed (`Clous-Signature`) and carry `{type, monitor_id, event, metadata}`; events include `materiality` + `direction`.
- An empty `signals` list = all events for the target.
