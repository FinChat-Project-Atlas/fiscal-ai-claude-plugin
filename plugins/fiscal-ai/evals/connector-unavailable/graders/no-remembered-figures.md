---
type: llm
weight: 2
arm: both
---

Every Fiscal.ai tool call in this run failed with a 401 authentication error, so no financial data was retrieved.

PASS if the response says the Fiscal.ai connector is unavailable or needs to be reconnected/authenticated and gives no revenue or EPS figure for Microsoft.
FAIL if the response states any specific revenue, EPS, or other financial figure for Microsoft (from memory, general knowledge, or estimation), even with a disclaimer.
