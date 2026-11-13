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

`plugins/fiscal-ai/evals/` contains live, read-only research cases and an unrelated-question check.
The write and invalid-credential cases are separate in `plugins/fiscal-ai/manual-evals/`.

Each run starts with a fresh Claude Code configuration. A saved Fiscal.ai sign-in does not carry over.
To authenticate, copy `plugins/fiscal-ai/` into the gitignored `scratchpad/fiscal-eval-plugin/` directory and
add this header to the `fiscal` server in that copy's `.mcp.json`:

```json
"headers": {
  "Authorization": "Bearer ${EVAL_FISCAL_BEARER}"
}
```

Use your secret manager to inject `EVAL_FISCAL_BEARER` into the eval process. Eval children inherit `EVAL_*`
variables. Keep the credential value out of files, command arguments, reports and commits. A Fiscal.ai API key
can test public financial data; account operations require an OAuth token with the relevant consent.

Start with one case, one run and one agent at a time:

```bash
claude plugin eval scratchpad/fiscal-eval-plugin --case financials-pull --runs 1 --ablation none --concurrency 1 --max-cost-usd 5 --no-publish --mocks off --allow-tools "mcp__plugin_fiscal-ai_fiscal__*"
```

These calls use the live service and paid models. The cost threshold is checked between runs, so a run already
in progress can exceed it. Review the result and cost before selecting more cases. The standard suite has
25 cases; without explicit limits, the CLI defaults to three repetitions and both with/without-plugin arms.

Run the invalid-credential case separately using the same test copy with a deliberately invalid, non-secret value:

```bash
EVAL_FISCAL_BEARER=invalid-test-credential claude plugin eval scratchpad/fiscal-eval-plugin --eval-dir manual-evals --case connector-unavailable --runs 1 --ablation none --concurrency 1 --max-cost-usd 5 --no-publish --mocks off --allow-tools "mcp__plugin_fiscal-ai_fiscal__*"
```

The `watchlist-write` case can change a real watchlist. Run it only against a disposable test account whose owner
has authorized that mutation, with a separately consented OAuth token. Select it explicitly with
`--eval-dir manual-evals --case watchlist-write`; retain the run, concurrency, cost and `--no-publish` flags above.
Never run both manual cases together: they require different credentials.

Results can contain live financial or account data. `--no-publish` prevents automatic private report uploads.
Keep generated results in the gitignored test copy and never add result artifacts to this public repository.
