---
type: llm
weight: 3
---

PASS if the response either reports a confirmed result returned by a watchlist helper, or says that adding to a watchlist is not available in this connection and explains what the user can do (for example reconnect the Fiscal.ai connector with the watchlist permission or use the Fiscal.ai app).
FAIL if it says the companies were added without a confirmed helper result, names or describes a watchlist helper it did not actually find, or gives instructions that pretend the change was made.
