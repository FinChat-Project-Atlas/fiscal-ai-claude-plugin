# Fiscal.ai agent plugin

The official Fiscal.ai plugin combines the production Fiscal.ai MCP with source-linked public-company research
workflows.

It supports company discovery, filings, financial statements, segments and KPIs, prices, capitalization, ratios,
news, earnings events and transcripts, fund letters, ownership, comparisons, screening, watchlists, financial
models, valuation, accounting quality, credit analysis, industry reports, and investment research.

## Claude Code

Add this repository as a marketplace:

```text
/plugin marketplace add FinChat-Project-Atlas/fiscal-ai-claude-plugin
```

Then install the plugin:

```text
/plugin install fiscal-ai@fiscal-ai
```

The plugin connects only to the production Fiscal.ai MCP at `https://api.fiscal.ai/mcp`. Available data and account
actions depend on the signed-in user's Fiscal.ai plan and live MCP entitlements.

## Documentation

- [Fiscal.ai MCP integration](https://docs.fiscal.ai/docs/guides/mcp-integration)
- [Fiscal.ai](https://fiscal.ai)
