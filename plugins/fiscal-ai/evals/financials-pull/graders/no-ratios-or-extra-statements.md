---
type: regex
target: mock_calls
pattern: 'codemode\.(company_ratios|company_stock_prices|top_news)\(|statementType:\s*\\?\"(balance-sheet|cash-flow-statement)'
match: not_contains
---
