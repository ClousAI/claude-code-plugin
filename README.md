<div align="center">

# Clous — Claude Code plugin

**Query and monitor public-data signals from inside Claude Code.**

Installs the **Clous MCP server** (49 tools) plus six ready-made **SEC analyst slash-commands** — entity-resolved, agent-native filing data with citations.

[![Docs](https://img.shields.io/badge/docs-clous.ai-blue)](https://docs.clous.ai)
[![MCP](https://img.shields.io/badge/MCP-49%20tools-6e56cf)](https://github.com/ClousAI/Mcp)
[![Built for AI agents](https://img.shields.io/badge/built%20for-AI%20agents-6e56cf)](https://clous.ai)
[![License: MIT](https://img.shields.io/badge/license-MIT-black)](./LICENSE)

[clous.ai](https://clous.ai) · [docs.clous.ai](https://docs.clous.ai)

</div>

---

## 30-second quickstart

In Claude Code:

```
/plugin marketplace add ClousAI/claude-code-plugin
/plugin install clous
```

Enter your **Clous API key** when prompted (`clous_live_...`). Get a free one at **[clous.ai](https://clous.ai)** — 100 credits, no card. Then try:

```
/clous:8k-triage NVDA,TSLA
```

**SEC/EDGAR is live today; Clous is expanding across public data.**

## Key features

- **Six SEC-analyst slash-commands** — purpose-built workflows, not raw tool calls.
- **49 MCP tools** — filing search, full-text, XBRL financials, insider trades, 13F, Form D, 8-K events, AI briefings, grounded Q&A, monitors/webhooks.
- **Cited by construction** — every answer carries the accession + EDGAR URL.
- **Local or hosted** — the same server runs via `npx -y @clousai/mcp` or hosted at [mcp.clous.ai](https://mcp.clous.ai).
- **Bring your own key** — open-source, no secrets bundled.

## Slash commands

| Command | What it does |
|---|---|
| `/clous:8k-triage <tickers>` | Triage recent 8-K material events — classify items, score materiality, flag signal vs. noise |
| `/clous:insider-signals <ticker>` | Read Form 3/4/5 insider activity, strip 10b5-1/automatic noise, flag clusters & notable buys |
| `/clous:13f-tracker <manager\|ticker>` | Quarter-over-quarter 13F position changes |
| `/clous:risk-diff <ticker>` | Year-over-year diff of 10-K Item 1A risk factors |
| `/clous:filing-briefing <accession>` | AI briefing — materiality, direction, what-it-means/what-to-watch |
| `/clous:set-monitor <request>` | Create a real-time monitor (ticker/CIK/form/event-type + webhook) |

## MCP server

The plugin wires the Clous MCP server via `npx -y @clousai/mcp` (stdio), using your configured `CLOUS_API_KEY`. The same server is hosted at `https://mcp.clous.ai/mcp` and works in **Cursor** and **Claude Desktop** directly — see [`Mcp`](https://github.com/ClousAI/Mcp).

## Zero-SDK integration

Any OpenAI client works against Clous — point it at `base_url=https://api.clous.ai/v1`, `model="clous"` for grounded, cited answers over the data.

## Part of the Clous platform

Clous is **public data intelligence for AI agents** — entity-resolved signals from public records and the web, monitored in real time, delivered with citations. SEC/EDGAR is live today; expanding across public data.

| | |
| --- | --- |
| **Website** | [clous.ai](https://clous.ai) |
| **Docs** | [docs.clous.ai](https://docs.clous.ai) · [`llms.txt`](https://docs.clous.ai/llms.txt) |
| **Claude Code plugin** | [`claude-code-plugin`](https://github.com/ClousAI/claude-code-plugin) ← you are here |
| **MCP server** | [`Mcp`](https://github.com/ClousAI/Mcp) · hosted at [mcp.clous.ai](https://mcp.clous.ai) |
| **Agent Skill** | [`skill`](https://github.com/ClousAI/skill) |
| **SDKs** | [`clous-python`](https://github.com/ClousAI/clous-python) · [`clous-js`](https://github.com/ClousAI/clous-js) |
| **Recipes** | [`cookbook`](https://github.com/ClousAI/cookbook) |
| **Framework tools** | [`integrations`](https://github.com/ClousAI/integrations) (LangChain · LlamaIndex · OpenAI · Vercel AI · CrewAI) |

## License

MIT — see [LICENSE](./LICENSE).
