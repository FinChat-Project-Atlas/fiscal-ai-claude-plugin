---
type: llm
weight: 3
---

PASS if the response is a compact overview of Microsoft that includes: what the business does, the latest fiscal-year revenue and diluted EPS labelled with the fiscal year (Microsoft's fiscal year ends June 30) and USD, market capitalization, at least one valuation multiple such as P/E or EV/EBITDA, and a link to Microsoft's Fiscal.ai company page of the form https://fiscal.ai/company/<identifier>.
FAIL if revenue or EPS is missing or has no period, if there is no fiscal.ai company link, if any link's address starts with https://api.fiscal.ai (a fiscal.ai audit link that carries an encoded API address in its query string is fine), or if the response says it cannot retrieve the data.
