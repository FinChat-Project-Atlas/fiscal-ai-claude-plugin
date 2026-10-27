---
type: llm
weight: 3
---

PASS if the response names one Tesla annual report (10-K) with its fiscal year and filing date, and gives a public link to it on sec.gov or Tesla's investor site.
FAIL if it gives a 10-Q, 8-K, or press release as the 10-K, gives no link, gives a link whose address starts with https://api.fiscal.ai or a raw PDF/base64 endpoint, or says no filing was found.
