# HolFin Excel Functions

Pull financial data directly into Excel and Google Sheets using HolFin formulas — no copy-pasting, no manual updates.

> **Platform:** Microsoft Excel
> All functions use dot `.` as separator: `=HOLFIN.INCOME(...)`

---

## Table of Contents

- [Authentication](#authentication)
- [Financial Statements](#financial-statements)
  - [Income Statement](#income-statement)
  - [Balance Sheet](#balance-sheet)
  - [Cash Flow](#cash-flow)
  - [Key Metrics](#key-metrics)
  - [Ratios](#ratios)
- [Individual Metrics](#individual-metrics)
- [Growth](#growth)
- [Share Price](#share-price)
- [Earnings](#earnings)
- [Parameters Reference](#parameters-reference)

---

## Authentication

You need a HolFin account to use these functions. Sign in via the HolFin sidebar panel or at [holfin.ai](https://holfin.ai).

Free accounts have limited data range. Upgrade to Pro for full history and all metrics.

---

## Financial Statements

All statement functions return a full table starting at the selected cell. Use `showHeaders: TRUE` to include column headers.

### Income Statement

```
=HOLFIN.INCOME(symbol, period, from, to, showHeaders)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol, e.g. `"AAPL"` |
| `period` | string | `"annual"` \| `"quarterly"` \| `"ttm"` |
| `from` | number | Start year, e.g. `2020` |
| `to` | number | End year, e.g. `2026` |
| `showHeaders` | boolean | `TRUE` to include headers (default: `FALSE`) |

**Examples**

```excel
=HOLFIN.INCOME("AAPL", "annual", 2020, 2024, TRUE)
=HOLFIN.INCOME("MSFT", "quarterly", 2023, 2024, FALSE)
=HOLFIN.INCOME("NVDA", "ttm", , , TRUE)
```

---

### Balance Sheet

```
=HOLFIN.BALANCE(symbol, period, from, to, showHeaders)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol, e.g. `"MSFT"` |
| `period` | string | `"annual"` \| `"quarterly"` \| `"ttm"` |
| `from` | number | Start year |
| `to` | number | End year |
| `showHeaders` | boolean | `TRUE` to include headers (default: `FALSE`) |

**Examples**

```excel
=HOLFIN.BALANCE("MSFT", "annual", 2020, 2024, TRUE)
=HOLFIN.BALANCE("TSLA", "quarterly", 2022, 2024, TRUE)
```

---

### Cash Flow

```
=HOLFIN.CASHFLOW(symbol, period, from, to, showHeaders)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol |
| `period` | string | `"annual"` \| `"quarterly"` \| `"ttm"` |
| `from` | number | Start year |
| `to` | number | End year |
| `showHeaders` | boolean | `TRUE` to include headers (default: `FALSE`) |

**Examples**

```excel
=HOLFIN.CASHFLOW("AMZN", "annual", 2018, 2024, TRUE)
=HOLFIN.CASHFLOW("GOOG", "ttm", , , TRUE)
```

---

### Key Metrics

```
=HOLFIN.KEYMETRICS(symbol, period, from, to, showHeaders)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol |
| `period` | string | `"annual"` \| `"quarterly"` \| `"ttm"` |
| `from` | number | Start year |
| `to` | number | End year |
| `showHeaders` | boolean | `TRUE` to include headers (default: `FALSE`) |

**Examples**

```excel
=HOLFIN.KEYMETRICS("AAPL", "annual", 2020, 2024, TRUE)
=HOLFIN.KEYMETRICS("META", "ttm", , , TRUE)
```

---

### Ratios

```
=HOLFIN.RATIOS(symbol, period, from, to, showHeaders)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol |
| `period` | string | `"annual"` \| `"quarterly"` \| `"ttm"` |
| `from` | number | Start year |
| `to` | number | End year |
| `showHeaders` | boolean | `TRUE` to include headers (default: `FALSE`) |

**Examples**

```excel
=HOLFIN.RATIOS("MSFT", "annual", 2020, 2024, TRUE)
=HOLFIN.RATIOS("JPM", "quarterly", 2023, 2024, TRUE)
```

---

## Individual Metrics

Pull a single metric across time instead of a full statement.

```
=HOLFIN.INCOME_METRIC(symbol, metric, period, from, to, showHeaders)
=HOLFIN.BALANCE_METRIC(symbol, metric, period, from, to, showHeaders)
=HOLFIN.CASHFLOW_METRIC(symbol, metric, period, from, to, showHeaders)
=HOLFIN.KEYMETRICS_METRIC(symbol, metric, period, from, to, showHeaders)
=HOLFIN.RATIOS_METRIC(symbol, metric, period, from, to, showHeaders)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol |
| `metric` | string | Metric name, e.g. `"revenue"`, `"netIncome"`, `"peRatio"` |
| `period` | string | `"annual"` \| `"quarterly"` \| `"ttm"` |
| `from` | number | Start year |
| `to` | number | End year |
| `showHeaders` | boolean | `TRUE` to include headers (default: `FALSE`) |

**Examples**

```excel
// Revenue history for Apple (annual, 2020–2024)
=HOLFIN.INCOME_METRIC("AAPL", "revenue", "annual", 2020, 2024, TRUE)

// Latest free cash flow for Microsoft
=HOLFIN.CASHFLOW_METRIC("MSFT", "freeCashFlow", "ttm")

// P/E ratio history for Tesla
=HOLFIN.RATIOS_METRIC("TSLA", "peRatio", "annual", 2018, 2024, TRUE)
```

> **Tip:** Leave `from` and `to` empty to get the latest single value.

---

## Growth

Retrieve growth rates for any metric — year-over-year, quarter-over-quarter, or multi-year CAGR.

```
=HOLFIN.INCOME_GROWTH(symbol, metric, growthType, period, from, to)
=HOLFIN.BALANCE_GROWTH(symbol, metric, growthType, period, from, to)
=HOLFIN.CASHFLOW_GROWTH(symbol, metric, growthType, period, from, to)
=HOLFIN.KEYMETRICS_GROWTH(symbol, metric, growthType, period, from, to)
=HOLFIN.RATIOS_GROWTH(symbol, metric, growthType, period, from, to)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol |
| `metric` | string | Metric name, e.g. `"revenue"`, `"eps"` |
| `growthType` | string | `"YoY"` \| `"QoQ"` \| `"CAGR3Y"` \| `"CAGR5Y"` \| `"CAGR10Y"` |
| `period` | string | `"annual"` \| `"quarterly"` |
| `from` | number | Start year (optional) |
| `to` | number | End year (optional) |

**Examples**

```excel
// Revenue YoY growth for Apple
=HOLFIN.INCOME_GROWTH("AAPL", "revenue", "YoY", "annual", 2020, 2024)

// EPS 5-year CAGR for Microsoft
=HOLFIN.INCOME_GROWTH("MSFT", "eps", "CAGR5Y", "annual")

// Quarterly QoQ net income growth for Nvidia
=HOLFIN.INCOME_GROWTH("NVDA", "netIncome", "QoQ", "quarterly", 2023, 2024)
```

---

## Share Price

Retrieve historical price data as a table or matrix.

```
=HOLFIN.PRICE(symbol, returnType, layout, frequency, from, to, showHeaders)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol |
| `returnType` | string | `"value"` \| `"pctChange"` \| `"absChange"` \| `"totalReturn"` |
| `layout` | string | `"list"` \| `"matrix"` |
| `frequency` | string | `"monthly"` \| `"annual"` |
| `from` | number | Start year, e.g. `2000` |
| `to` | number | End year, e.g. `2026` |
| `showHeaders` | boolean | `TRUE` to include headers (default: `FALSE`) |

**Return types**

| Value | Description |
|---|---|
| `"value"` | Absolute price (monthly close) |
| `"pctChange"` | Percentage change vs. prior period |
| `"absChange"` | Absolute change vs. prior period |
| `"totalReturn"` | Price return adjusted for dividends |

**Examples**

```excel
// Monthly close prices for Microsoft (2020–2024)
=HOLFIN.PRICE("MSFT", "value", "list", "monthly", 2020, 2024, TRUE)

// Annual total return matrix for Apple
=HOLFIN.PRICE("AAPL", "totalReturn", "matrix", "annual", 2015, 2024, TRUE)

// Monthly % change for Nvidia
=HOLFIN.PRICE("NVDA", "pctChange", "list", "monthly", 2022, 2024, TRUE)
```

---

## Earnings

Retrieve historical earnings data including EPS actuals, estimates and revenue surprise.

```
=HOLFIN.EARNINGS(symbol, quarters, showHeaders)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Ticker symbol |
| `quarters` | number | Number of past quarters, e.g. `20` (default: `20`) |
| `showHeaders` | boolean | `TRUE` to include headers (default: `TRUE`) |

**Output columns**

| Column | Description |
|---|---|
| Date | Earnings report date |
| EPS Actual | Reported EPS |
| EPS Estimate | Analyst consensus estimate |
| EPS Surprise % | Beat/miss vs. estimate |
| Revenue Actual | Reported revenue |
| Revenue Estimate | Analyst revenue estimate |
| Revenue Surprise % | Beat/miss vs. estimate |

**Examples**

```excel
// Last 20 quarters of earnings for Microsoft
=HOLFIN.EARNINGS("MSFT", 20, TRUE)

// Last 8 quarters for Apple
=HOLFIN.EARNINGS("AAPL", 8, TRUE)
```

---

## Parameters Reference

### Period values

| Value | Description |
|---|---|
| `"annual"` | Full fiscal year |
| `"quarterly"` | Individual quarters |
| `"ttm"` | Trailing twelve months |

### Growth types

| Value | Description |
|---|---|
| `"YoY"` | Year-over-year change |
| `"QoQ"` | Quarter-over-quarter change |
| `"CAGR3Y"` | 3-year compound annual growth rate |
| `"CAGR5Y"` | 5-year compound annual growth rate |
| `"CAGR10Y"` | 10-year compound annual growth rate |

### Platform separator

| Platform | Separator | Example |
|---|---|---|
| Google Sheets | `_` (underscore) | `=HOLFIN.INCOME("AAPL", ...)` |
| Excel | `.` (dot) | `=HOLFIN.INCOME("AAPL", ...)` |

---

## Need help?

- 📖 Full documentation: [holfin.ai/docs](https://holfin.ai/docs)
- 💬 Support: [support@holfin.ai](mailto:support@holfin.ai)
- 🌐 Website: [holfin.ai](https://holfin.ai)
