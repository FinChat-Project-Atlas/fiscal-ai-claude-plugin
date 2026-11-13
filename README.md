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

## Evals

`plugins/fiscal-ai/evals/` holds a `claude plugin eval` suite that runs against the live Fiscal.ai MCP. It covers
retrieval (statements, filings, prices, segments, news, ownership, transcripts, fund letters), analysis (comparisons,
valuation, credit, quality scores, a bank model, a screen), guardrails (unavailable connector, account writes, free-plan
limits), and when the skill should and should not trigger.

Each case pairs an outcome rubric with a check that the figures in the answer match the data the MCP returned, plus
with-plugin-only checks on which Fiscal helpers were called. The cases call the real server, so start it and grant
its tools:

```bash
claude plugin eval plugins/fiscal-ai --mocks off --allow-tools "mcp__plugin_fiscal-ai_fiscal__*"
```

Each eval run starts with a fresh Claude Code configuration, so a saved Fiscal.ai sign-in does not carry over to it.
The `connector-unavailable` case expects the connector's credential to be rejected. Results contain live Fiscal.ai
data and stay in the gitignored `evals/results/`.
