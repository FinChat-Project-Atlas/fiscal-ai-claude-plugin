# Fiscal.ai Trial Companies

The free plan covers a set list of trial companies, and the list changes over time. The current list, with company
keys, is on the Free Trial page: https://docs.fiscal.ai/docs/guides/free-trial.md. It is the list the API enforces,
so use it rather than memory.

- With web access, read that page before a trial tour and use only company keys it lists.
- Without web access, a call for a company outside the trial fails with a 403 saying the company is not available
  on the plan. Treat that as the answer: don't retry that company, and run the tour with a substitute below.

Suggested substitutions. Use them without asking; a 403 on one means it has left the trial, so try the other:

- `NYSE_CMG` -> `NASDAQ_MSFT` or `NASDAQ_GOOG`
- `NYSE_NET` -> `NASDAQ_MSFT`
- APAC home-market listings -> `NYSE_SONY`, `NASDAQ_ASML`, or `NYSE_SHEL` if the user wants international exposure
