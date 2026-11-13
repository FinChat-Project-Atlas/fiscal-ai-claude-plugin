---
type: llm
weight: 3
---

The skill must ask before fanning out fundamental calls to more than 20 candidate companies, so either outcome below passes.

PASS if the response states the screen definition (universe, operating-margin metric and period, growth metric), reports how many companies were in the universe and how many survived, gives a ranked table with operating margin and revenue growth, and discloses companies excluded for missing data, entitlement errors, or a call budget.
Also PASS if, after building the candidate universe from retrieved data, it reports the universe and candidate counts, explains that more than 20 candidates need fundamental calls, and stops to ask the user with concrete narrowing or full-screen options instead of ranking a silent subset.
FAIL if it presents a ranked list without universe and survivor counts, silently stops at an arbitrary number of companies, ranks companies from memory, or says the data is unavailable without trying.
