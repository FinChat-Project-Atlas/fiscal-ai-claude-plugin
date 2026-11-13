---
type: llm
weight: 2
focus: trace
---

The trace is a Claude session that may have called the Fiscal.ai `execute_code` tool. Its tool results are JSON (escaped inside the trace) with raw values, usually in whole currency units, which the final answer may round or scale to thousands, millions, or billions.

PASS if the company-specific figures in Claude's final answer are consistent with the `execute_code` results you can see, allowing rounding, unit scaling, and arithmetic derived from those values. An answer that gives no company figures passes this check.
FAIL if the final answer states company figures although no `execute_code` call in the trace returned data, or if a figure clearly contradicts a value you can see in the tool results (for example a different revenue for the same company and period). Do not fail because a figure's source result is elided or not visible to you, or because a figure is a derived calculation.

Amendments (10-K/A, or a documentType ending in "(Amended)") are not original 10-Ks. Also FAIL if the trace's filing catalog contains an original 10-K with a later filing date than the one the answer presents as most recent, if the link in the answer is not the sourceUrl of the chosen filing, or if the catalog has a later amendment for the chosen fiscal year and the answer does not mention it.
