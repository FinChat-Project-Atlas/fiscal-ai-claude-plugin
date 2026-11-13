---
description: 'Filing finder filters the catalog for the newest 10-K, links the public sourceUrl, and never fetches a PDF.'
tags: [retrieval, filings]
max_turns: 20
timeout_seconds: 600
allowed_tools: [Read, Glob, Grep, Skill]
---

Find me Tesla's most recent 10-K and give me a link to it.
