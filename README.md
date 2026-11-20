# Basko for AI assistants

[Basko](https://basko.app) compares grocery and pharmacy prices across stores in Uzbekistan,
Kazakhstan, Russia, the United States and the United Kingdom. This repository connects Basko
to AI assistants: one remote MCP server, plus skills for the common jobs.

| | |
| --- | --- |
| MCP server | `https://mcp.basko.app/mcp` (Streamable HTTP, no account needed) |
| Tools | `search_products`, `get_product`, `compare_basket`, `find_swaps`, `get_deals`, `find_stores` (all read-only) |
| Skills | `basko-weekly-shop`, `basko-price-check`, `basko-list-compare` |
| Countries | UZ, KZ, RU, US, UK |

## Install

**Claude Code**

```bash
claude plugin marketplace add bekroz/basko-ai
claude plugin install basko@basko
```

or the server alone: `claude mcp add --transport http basko https://mcp.basko.app/mcp`

**Claude (web, desktop, mobile)**: Settings › Connectors › Add custom connector, with the
address `https://mcp.basko.app/mcp`.

**ChatGPT**: add Basko from the Plugin directory once it's listed. Until then, with developer
mode on, add a custom connector with the address `https://mcp.basko.app/mcp`.

**Codex**

```bash
codex plugin marketplace add bekroz/basko-ai
```

**Gemini CLI**

```bash
gemini extensions install https://github.com/bekroz/basko-ai
```

**Any other MCP client**: point it at `https://mcp.basko.app/mcp` (Streamable HTTP).

More, in Uzbek, Russian and English: [basko.app/ai](https://basko.app/en/ai).

## What you can ask

- "Plan dinners for four this week in Tashkent, under 400,000 so'm."
- "Is £1.65 a good price for 4 pints of milk?"
- "Where is this list cheapest in Almaty: milk, eggs, bread, buckwheat, chicken?"
- "Cheaper swaps for my Walmart list?"

## What Basko sees

Assistants see only what a Basko tool returns, and Basko sees only what a tool is sent; the rest
of the chat stays with the assistant. The tools take no personal data. Basko logs which tool was
used, the country, how many results, how long it took and which assistant asked; search words are
kept for 30 days without anything that identifies a person.

Prices come from Basko's own database (store APIs and feeds, open price data and receipts shared
by shoppers). The tools never fetch a store's website during a chat. Results are ordered by price
and distance only. Store links go through basko.app, and Basko may earn a commission from some
stores; it never changes the order.

[Privacy policy](https://basko.app/en/privacy) · [Terms](https://basko.app/en/terms) ·
[Support](https://basko.app/en/support)

## Layout

| Path | For |
| --- | --- |
| `.claude-plugin/` | Claude Code and Claude's plugin directory (`plugin.json`, `marketplace.json`) |
| `.mcp.json` | the MCP server, for Claude |
| `plugin.json`, `mcp.json`, `.agents/plugins/marketplace.json` | Codex and ChatGPT plugins |
| `gemini-extension.json`, `GEMINI.md` | Gemini CLI |
| `skills/` | the skills, in the [Agent Skills](https://agentskills.io/specification) format, shared by all of them |

Published by BEKRZ MCHJ. MIT licence.
