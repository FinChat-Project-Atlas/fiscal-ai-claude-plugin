---
type: llm
weight: 2
---

The tool data said NVIDIA revenue (USD): FY2026 214.9 billion, FY2025 130.5 billion, FY2024 60.9 billion, with an auditUrl per year of the form https://fiscal.ai/audit/NasdaqGS-NVDA/<year>/income-statement.

PASS if the response lists the three most recent fiscal years with revenue matching those figures (rounding to billions is fine), states USD and the unit, labels the fiscal years, and provides the fiscal.ai audit source link for each year.
FAIL if any revenue figure differs from the tool data, if a year is missing, if the links are api.fiscal.ai or made-up SEC URLs instead of the audit links, or if the response says the data is unavailable.
