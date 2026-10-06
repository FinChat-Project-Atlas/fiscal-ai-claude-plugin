# Fiscal.ai API

Company identifiers use the format `<EXCHANGE>_<TICKER>`, e.g. `NASDAQ_MSFT`, `NYSE_JPM`.

## Requested functions
Call via `codemode.<name>({...})` inside the execute_code tool.

declare const codemode: {
  companies_list: (input: { pageNumber?: number; pageSize?: number }) => Promise<{ pagination: { pageNumber: number; pageSize: number; totalPages: number; hasNextPage: boolean }; data: Array<{ companyKey: string; name: string; ticker: string; exchangeName: string; country: string }> }>;
  company_profile: (input: { companyKey: string }) => Promise<{ companyKey: string; name: string; description: string; sector: string; industry: string; country: string; reportingCurrency: string; tradingCurrency: string; reportingTemplate: "standard" | "financials" | "insurance" | "real-estate" | "utilities" | "capital-markets"; fiscalIdentifier: string; terminalUrl: string }>;
  company_peers: (input: { companyKey: string }) => Promise<{ companyKey: string; peers: Array<{ companyKey: string; name: string; relationshipType: string }> }>;
  company_financials_standardized: (input: { statementType: "income-statement" | "balance-sheet" | "cash-flow-statement"; companyKey: string; periodType?: string; currency?: string }) => Promise<{ metrics: Array<{ metricId: string; name: string; unit: string }>; data: Array<{ fiscalYear: number; fiscalQuarter: number | null; periodType: string; reportDate: string; currency: string; metricsValues: Record<string, { value: number | null; asReportedValues?: Array<{ sources: Array<{ auditUrl: string; originalSourceUrl: string; pageNumber: number }> }> }> }> }>;
  company_ratios: (input: { companyKey: string; periodType?: string; currency?: string }) => Promise<{ metrics: Array<{ metricId: string; ratioId: string; name: string }>; data: Array<{ periodType: string; reportDate: string; metricValues: Record<string, number | null> }> }>;
  company_stock_prices: (input: { companyKey: string }) => Promise<{ listingFiscalIdentifier: string; ticker: string; exchangeCode: string; tradingCurrency: string; tradingStatus: string; prices: Array<{ date: string; openPrice: number; closePrice: number; volume: number }> }>;
  company_filings: (input: { companyKey: string }) => Promise<Array<{ filingId: string; documentType: string; secFormType: string | null; filingDate: string; reportDate: string; fiscalYear: number; fiscalQuarter: number | null; sourceUrl: string; pdfUrl: string }>>;
  filing_page_image: (input: { filingId: string; pageNumber: number; companyKey: string }) => Promise<unknown>;
  filing_pdf: (input: { filingId: string; companyKey: string }) => Promise<unknown>;
  top_news: (input: { companyKey?: string; minImportance?: number; maxImportance?: number; pageSize?: number; pageNumber?: number }) => Promise<{ pagination: { hasNextPage: boolean }; data: Array<{ title: string; publishedAt: string; importance: number; eventType: string; url: string }> }>;
  company_news: (input: { companyKey: string; startDate?: string; endDate?: string; importance?: number }) => Promise<{ pagination: { hasNextPage: boolean }; data: Array<{ title: string; publishedAt: string; importance: number; url: string }> }>;
};

Available functions: companies_list, company_profile, company_news, company_peers, top_news, company_earnings_summary, company_financials_as_reported, standardized_metrics_list, all_standardized_metrics_list, company_financials_standardized, ratios_list, company_ratios, company_daily_ratios, company_shares_outstanding, company_stock_splits, company_stock_prices, company_segments_and_kpis, company_adjusted_metrics, company_filings, filing_page_image, filing_pdf, company_ir_events, company_ir_events_transcript, company_insider_holders, company_insider_transactions, company_institutional_holders, holder_institutional_holdings, institutional_holders_list, company_fund_letters, fund_letters, fund_letter.

## Usage notes
- Pass plain JavaScript in exactly this shape: `async () => { ... }`
- The sandbox is network-isolated and limited to 30 seconds; use only injected `codemode.*` functions
- Run at most six independent helper promises at once
- Emit one compact payload with `console.log(JSON.stringify(result))`; do not also return it
- Financials endpoints return `{ metrics, data }`; `data[].metricsValues` is keyed by metric ID
