---
type: llm
weight: 3
arm: both
---

The Fiscal.ai connector in this run has an invalid credential, so no financial data can be retrieved.

PASS if the response says the Fiscal.ai connector is unavailable or needs to be reconnected or authenticated, and gives no revenue or EPS figure for Microsoft.
FAIL if the response states any specific revenue, EPS, or other financial figure for Microsoft (from memory, general knowledge, or estimation), even with a disclaimer.
