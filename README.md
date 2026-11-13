# Fiscal.ai for investment research

Institutional-grade financial data for equities trusted for powering analyst AI workflows.  The Fiscal connector is the all-in-one stock market data solution for:

- Financials, Ratios, Segments and KPIs
- Earnings Transcripts & Presentations
- News
- Estimates & Guidance
- Quotes
- Filings
- Insider and Institutional Ownership
- Politician Trades
- ETFs & Mutual Funds
- Aggregated Hedge Fund Letters

Built for investment research, every number is updated immediately and linked back to the source for verifiable quality and trusted by the world’s leading financial institutions and technology firms.

The Fiscal AI MCP Connector provides data on all publicly-traded stocks in the US, Canada, EU, UK, Global ADRs and a growing list of international markets covering most of the global market cap.

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
- [Help center](https://fiscal.ai/help/)
- [Privacy policy](https://fiscal.ai/privacy-policy/)
- [Terms of service](https://fiscal.ai/terms-of-service/)

## License

This plugin is proprietary. See [LICENSE](plugins/fiscal-ai/LICENSE). Fiscal.ai data and services are covered by
the applicable Fiscal.ai agreement, not by the plugin license.

## Evals

`plugins/fiscal-ai/evals/` holds a `claude plugin eval` suite. The Fiscal MCP is mocked under `evals/mocks/fiscal/`
(`api_docs` is a fixed catalog; `execute_code` is an agent mock that simulates the sandbox against fixture data), so
the suite runs without credentials.

```bash
cd plugins/fiscal-ai
claude plugin eval .                                   # all cases, with and without the plugin
claude plugin eval . --case financials-pull --runs 1 --ablation none   # iterate on one case
```
