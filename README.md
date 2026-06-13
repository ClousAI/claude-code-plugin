# Clous — Claude Code plugin

Query and monitor **SEC / EDGAR filings** directly in Claude Code. Powered by the [Clous API](https://clous.ai) — entity-resolved, agent-native filing data.

Installing this plugin registers the **Clous MCP server** (49 tools) and adds six ready-made **SEC analyst slash-commands**.

## Install

In Claude Code:

```
/plugin marketplace add clousai/claude-code-plugin
/plugin install clous
```

Then enter your **Clous API key** when prompted (`clous_live_...`). Get a free key at **[clous.ai](https://clous.ai)** — 100 free credits, no card.

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

The plugin wires the Clous MCP server via `npx -y @clous/mcp` (stdio), using your configured `CLOUS_API_KEY`. The same server is also available hosted at `https://mcp.clous.ai/mcp` and works in **Cursor** and **Claude Desktop** directly — see [github.com/clousai/Mcp](https://github.com/clousai/Mcp).

The 49 tools cover filing search, full-text, financials (XBRL), insider trades, 13F holdings, Form D, advisers, 8-K events, AI briefings, grounded Q&A, and monitors/webhooks.

## Also: zero-SDK integration

Any OpenAI client works against Clous — point it at `base_url=https://api.clous.ai/v1`, `model="clous"` for grounded, cited answers over filings.

## Resources
- Docs: [docs.clous.ai](https://docs.clous.ai) · machine spec: [docs.clous.ai/llms.txt](https://docs.clous.ai/llms.txt)
- MCP server: [github.com/clousai/Mcp](https://github.com/clousai/Mcp)

## License
MIT — see [LICENSE](./LICENSE).
