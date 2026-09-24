# HolFin Excel Functions

Pull financial data directly into MS Excel™ using HolFin formulas — no copy-pasting, no manual updates.

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
- [Growth](#growth)
  - [Income Statement Growth](#income-statement-growth)
  - [Balance Sheet Growth](#balance-sheet-growth)
  - [Cash Flow Growth](#cash-flow-growth)
  - [Key Metrics Growth](#key-metrics-growth)
  - [Ratios Growth](#ratios-growth)
- [Comparison Table](#comparison-table)
- [Share Price](#share-price)
- [Earnings](#earnings)
- [Dividends & Splits](#dividends--splits)
  - [Dividends](#dividends)
  - [Splits](#splits)
- [ETFs](#etfs)
  - [ETF Overview](#etf-overview)
  - [ETF Holdings](#etf-holdings)
  - [ETF Price](#etf-price)
- [Sectors](#sectors)
  - [Sector Performance](#sector-performance)
  - [Sector Breakdown](#sector-breakdown)
  - [Sector Boxplot](#sector-boxplot)
- [Market Data](#market-data)
  - [Forex](#forex)
  - [Commodities](#commodities)
  - [Crypto](#crypto)
  - [Economic Indicator](#economic-indicator)
- [Parameters Reference](#parameters-reference)

---

## Authentication

You need a HolFin account to use these functions. Sign in via the HolFin sidebar panel or at [holfin.ai](https://holfin.ai).

Free accounts have limited data range. Upgrade to Pro for full history and all metrics.

---

## Financial Statements

All statement functions return a full table starting at the selected cell. Use `showHeader: TRUE` to include column headers.

### Income Statement

```
=HOLFIN.INCOME(symbol, period, fromYear, toYear, showHeader, formatted)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol, e.g. `"AAPL"` |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year, e.g. `2020` |
| `toYear` | number | End year, e.g. `2024` |
| `showHeader` | boolean | Include header row (`TRUE` by default) |
| `formatted` | boolean | Scale numbers to B/M/K (`FALSE` by default) |

**Examples**

```excel
=HOLFIN.INCOME("AAPL", "Annual", 2020, 2024, TRUE)
=HOLFIN.INCOME("MSFT", "Quarterly", 2023, 2024, FALSE)
=HOLFIN.INCOME("NVDA", "TTM")
```

---

### Balance Sheet

```
=HOLFIN.BALANCE(symbol, period, fromYear, toYear, showHeader, formatted)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol, e.g. `"MSFT"` |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |
| `showHeader` | boolean | Include header row (`TRUE` by default) |
| `formatted` | boolean | Scale numbers to B/M/K (`FALSE` by default) |

**Examples**

```excel
=HOLFIN.BALANCE("MSFT", "Annual", 2020, 2024, TRUE)
=HOLFIN.BALANCE("TSLA", "Quarterly", 2022, 2024, TRUE)
```

---

### Cash Flow

```
=HOLFIN.CASHFLOW(symbol, period, fromYear, toYear, showHeader, formatted)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |
| `showHeader` | boolean | Include header row (`TRUE` by default) |
| `formatted` | boolean | Scale numbers to B/M/K (`FALSE` by default) |

**Examples**

```excel
=HOLFIN.CASHFLOW("AMZN", "Annual", 2018, 2024, TRUE)
=HOLFIN.CASHFLOW("GOOG", "TTM")
```

---

### Key Metrics

```
=HOLFIN.KEYMETRICS(symbol, period, fromYear, toYear, showHeader, formatted)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |
| `showHeader` | boolean | Include header row (`TRUE` by default) |
| `formatted` | boolean | Scale numbers to B/M/K (`FALSE` by default) |

**Examples**

```excel
=HOLFIN.KEYMETRICS("AAPL", "Annual", 2020, 2024, TRUE)
=HOLFIN.KEYMETRICS("META", "TTM")
```

---

### Ratios

```
=HOLFIN.RATIOS(symbol, period, fromYear, toYear, showHeader, formatted)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |
| `showHeader` | boolean | Include header row (`TRUE` by default) |
| `formatted` | boolean | Scale numbers to B/M/K (`FALSE` by default) |

**Examples**

```excel
=HOLFIN.RATIOS("MSFT", "Annual", 2020, 2024, TRUE)
=HOLFIN.RATIOS("JPM", "Quarterly", 2023, 2024, TRUE)
```

---

## Growth

Retrieve growth rates for a single metric — year-over-year, quarter-over-quarter, or multi-year CAGR. `metric` must match a row label from the corresponding statement exactly.

### Income Statement Growth

```
=HOLFIN.INCOME_GROWTH(symbol, metric, growthType, period, fromYear, toYear)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `metric` | string | Metric name as shown in the statement, e.g. `"Revenue"` |
| `growthType` | string | `YoY` (default) \| `QoQ` \| `CAGR3Y` \| `CAGR5Y` \| `CAGR10Y` |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |

**Examples**

```excel
// Revenue YoY growth for Apple
=HOLFIN.INCOME_GROWTH("AAPL", "Revenue", "YoY", "Annual", 2020, 2024)

// EPS 5-year CAGR for Microsoft
=HOLFIN.INCOME_GROWTH("MSFT", "EPS", "CAGR5Y", "Annual")
```

---

### Balance Sheet Growth

```
=HOLFIN.BALANCE_GROWTH(symbol, metric, growthType, period, fromYear, toYear)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `metric` | string | Metric name as shown in the statement, e.g. `"Total Assets"` |
| `growthType` | string | `YoY` (default) \| `QoQ` \| `CAGR3Y` \| `CAGR5Y` \| `CAGR10Y` |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |

**Examples**

```excel
// Total assets 3-year CAGR for Microsoft
=HOLFIN.BALANCE_GROWTH("MSFT", "Total Assets", "CAGR3Y", "Annual")
```

---

### Cash Flow Growth

```
=HOLFIN.CASHFLOW_GROWTH(symbol, metric, growthType, period, fromYear, toYear)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `metric` | string | Metric name as shown in the statement, e.g. `"Operating cash flow"` |
| `growthType` | string | `YoY` (default) \| `QoQ` \| `CAGR3Y` \| `CAGR5Y` \| `CAGR10Y` |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |

**Examples**

```excel
// Operating cash flow YoY growth for Amazon
=HOLFIN.CASHFLOW_GROWTH("AMZN", "Operating cash flow", "YoY", "Annual", 2020, 2024)
```

---

### Key Metrics Growth

```
=HOLFIN.KEYMETRICS_GROWTH(symbol, metric, growthType, period, fromYear, toYear)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `metric` | string | Metric name as shown in the statement, e.g. `"Market Cap"` |
| `growthType` | string | `YoY` (default) \| `QoQ` \| `CAGR3Y` \| `CAGR5Y` \| `CAGR10Y` |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |

**Examples**

```excel
// Market cap 5-year CAGR for Meta
=HOLFIN.KEYMETRICS_GROWTH("META", "Market Cap", "CAGR5Y", "Annual")
```

---

### Ratios Growth

```
=HOLFIN.RATIOS_GROWTH(symbol, metric, growthType, period, fromYear, toYear)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `metric` | string | Metric name as shown in the statement, e.g. `"peRatioTTM"` |
| `growthType` | string | `YoY` (default) \| `QoQ` \| `CAGR3Y` \| `CAGR5Y` \| `CAGR10Y` |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |

**Examples**

```excel
// P/E ratio QoQ change for Tesla
=HOLFIN.RATIOS_GROWTH("TSLA", "peRatioTTM", "QoQ", "Quarterly", 2023, 2024)
```

---

## Comparison Table

Pull one or more metrics for one or more symbols side by side.

```
=HOLFIN.METRICS(symbols, metrics, period, fromYear, toYear, formatted, growth, growthOnly)
```

| Parameter | Type | Description |
|---|---|---|
| `symbols` | string | Comma-separated ticker symbols, e.g. `"AAPL,MSFT,GOOGL"` |
| `metrics` | string | Comma-separated metric names, e.g. `"Revenue,Net Income"` |
| `period` | string | `Annual` (default) \| `Quarterly` \| `TTM` |
| `fromYear` | number | Start year |
| `toYear` | number | End year |
| `formatted` | boolean | Scale numbers to B/M/K (`FALSE` by default) |
| `growth` | boolean | Add a QoQ/YoY % change column per symbol (`FALSE` by default) |
| `growthOnly` | boolean | Show only the % change columns, omit raw values (`FALSE` by default) |

**Examples**

```excel
// Revenue and Net Income for three companies, 2022–2024
=HOLFIN.METRICS("AAPL,MSFT,GOOGL", "Revenue,Net Income", "Annual", 2022, 2024)

// Same, with a YoY growth column per symbol
=HOLFIN.METRICS("AAPL,MSFT,GOOGL", "Revenue", "Annual", 2020, 2024, FALSE, TRUE)
```

---

## Share Price

Retrieve historical price data as a table or matrix.

```
=HOLFIN.PRICE(symbol, ret, layout, freq, fromYear, toYear, showHeader)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `ret` | string | `value` (default, close price) \| `pct` (MoM % change) \| `abs` (MoM ± change) \| `tr` (total return, adj. for dividends) |
| `layout` | string | `matrix` (year×month grid, default) \| `list` (time series) — ignored when `ret="tr"` |
| `freq` | string | `monthly` (default) \| `annual` — only used when `ret="tr"` |
| `fromYear` | number | Start year (default `2000`) |
| `toYear` | number | End year (default current year) |
| `showHeader` | boolean | Include header row (`TRUE` by default) |

**Examples**

```excel
// Monthly close prices for Microsoft (2020–2024), matrix layout
=HOLFIN.PRICE("MSFT", "value", "matrix", , 2020, 2024, TRUE)

// Annual total return for Apple
=HOLFIN.PRICE("AAPL", "tr", , "annual", 2015, 2024, TRUE)

// Monthly % change for Nvidia, time series layout
=HOLFIN.PRICE("NVDA", "pct", "list", , 2022, 2024, TRUE)
```

---

## Earnings

Retrieve historical earnings data including EPS actuals, estimates and revenue surprise.

```
=HOLFIN.EARNINGS(symbol, limit, showHeader, formatted)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `limit` | number | Number of past quarters, e.g. `20` (default `20`) |
| `showHeader` | boolean | Include header row (`TRUE` by default) |
| `formatted` | boolean | Format revenue numbers to B/M/K (`FALSE` by default) |

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

// Last 8 quarters for Apple, formatted
=HOLFIN.EARNINGS("AAPL", 8, TRUE, TRUE)
```

---

## Dividends & Splits

### Dividends

```
=HOLFIN.DIVIDENDS(symbol, limit, showHeader)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `limit` | number | Number of dividend events to return (default `40`) |
| `showHeader` | boolean | Include header row (`TRUE` by default) |

Returns ex-date, adjusted dividend, dividend and yield per payment.

**Examples**

```excel
=HOLFIN.DIVIDENDS("KO", 40, TRUE)
```

---

### Splits

```
=HOLFIN.SPLITS(symbol, showHeader)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Stock ticker symbol |
| `showHeader` | boolean | Include header row (`TRUE` by default) |

Returns date, numerator and denominator per split.

**Examples**

```excel
=HOLFIN.SPLITS("AAPL", TRUE)
```

---

## ETFs

### ETF Overview

```
=HOLFIN.ETFOVERVIEW(symbol, showHeader)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | ETF ticker symbol, e.g. `"SPY"` |
| `showHeader` | boolean | Include header row (`TRUE` by default) |

Returns AUM, expense ratio, holdings count and sector/asset allocation.

**Examples**

```excel
=HOLFIN.ETFOVERVIEW("SPY", TRUE)
```

---

### ETF Holdings

```
=HOLFIN.ETFHOLDINGS(symbol, limit, showHeader)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | ETF ticker symbol |
| `limit` | number | Number of holdings to return (default `25`) |
| `showHeader` | boolean | Include header row (`TRUE` by default) |

Returns ticker, name, weight % and shares for the current holdings.

**Examples**

```excel
=HOLFIN.ETFHOLDINGS("QQQ", 25, TRUE)
```

---

### ETF Price

```
=HOLFIN.ETFPRICE(symbol, fromYear, toYear, showHeader)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | ETF ticker symbol |
| `fromYear` | number | Start year (default `2000`) |
| `toYear` | number | End year (default current year) |
| `showHeader` | boolean | Include header row (`TRUE` by default) |

Returns yearly ETF price history.

**Examples**

```excel
=HOLFIN.ETFPRICE("SPY", 2015, 2024, TRUE)
```

---

## Sectors

### Sector Performance

```
=HOLFIN.SECTOR(symbol, metric, fromYear, toYear, view)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Sector ETF symbol, e.g. `"XLK"` (Technology), `"XLF"` (Financials) |
| `metric` | string | `momentum` (default) \| `spy` (vs. S&P 500) \| `drawdowns` \| `volatility` |
| `fromYear` | number | Start year (default `2010`) |
| `toYear` | number | End year (default current year) |
| `view` | string | `matrix` (year×month grid, default) \| `table` (time series) |

**Examples**

```excel
=HOLFIN.SECTOR("XLK", "momentum", 2015, 2024, "matrix")
```

---

### Sector Breakdown

```
=HOLFIN.SECTORBREAKDOWN(sectorName)
```

| Parameter | Type | Description |
|---|---|---|
| `sectorName` | string | Sector name, e.g. `"Technology"`, `"Financials"`, `"Energy"` |

Returns ticker, name, price, change %, market cap and free float for the sector's holdings.

**Examples**

```excel
=HOLFIN.SECTORBREAKDOWN("Technology")
```

---

### Sector Boxplot

```
=HOLFIN.SECTORBOXPLOT(metric)
```

| Parameter | Type | Description |
|---|---|---|
| `metric` | string | Metric column name, e.g. `"peRatioTTM"`, `"revenueGrowthYOY"` |

Returns min, Q1, median, Q3 and max for the metric across all 11 sectors.

**Examples**

```excel
=HOLFIN.SECTORBOXPLOT("peRatioTTM")
```

---

## Market Data

### Forex

```
=HOLFIN.FOREX(symbol, fromYear, toYear, view, mode)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Forex pair symbol, e.g. `"EURUSD"` |
| `fromYear` | number | Start year (default `2000`) |
| `toYear` | number | End year (default current year - 1) |
| `view` | string | `matrix` (year×month grid, default) \| `table` (time series) |
| `mode` | string | `value` (default) \| `pct` (MoM % change) \| `abs` (± change) |

**Examples**

```excel
=HOLFIN.FOREX("EURUSD", 2020, 2024, "matrix", "value")
```

---

### Commodities

```
=HOLFIN.COMMODITY(symbol, fromYear, toYear, view, mode)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Commodity symbol, e.g. `"GCUSD"` (Gold) |
| `fromYear` | number | Start year (default `2000`) |
| `toYear` | number | End year (default current year - 1) |
| `view` | string | `matrix` (year×month grid, default) \| `table` (time series) |
| `mode` | string | `value` (default) \| `pct` (MoM % change) \| `abs` (± change) |

**Examples**

```excel
=HOLFIN.COMMODITY("GCUSD", 2015, 2024, "table", "pct")
```

---

### Crypto

```
=HOLFIN.CRYPTO(symbol, fromYear, toYear, view, mode)
```

| Parameter | Type | Description |
|---|---|---|
| `symbol` | string | Crypto symbol, e.g. `"BTCUSD"` |
| `fromYear` | number | Start year (default `2015`) |
| `toYear` | number | End year (default current year - 1) |
| `view` | string | `matrix` (year×month grid, default) \| `table` (time series) |
| `mode` | string | `value` (default) \| `pct` (MoM % change) \| `abs` (± change) |

**Examples**

```excel
=HOLFIN.CRYPTO("BTCUSD", 2018, 2024, "matrix", "value")
```

---

### Economic Indicator

```
=HOLFIN.ECONINDICATOR(name, fromYear, toYear, view, mode, adaptFreq)
```

| Parameter | Type | Description |
|---|---|---|
| `name` | string | Indicator name, e.g. `"gdp"` or `"cpi"` |
| `fromYear` | number | Start year (default `2000`) |
| `toYear` | number | End year (default current year - 1) |
| `view` | string | `matrix` (default) \| `table` (time series) |
| `mode` | string | `value` (default) \| `pct` (% change) \| `abs` (± change) |
| `adaptFreq` | boolean | Adapt matrix layout to the indicator's frequency — monthly/quarterly/annual (`TRUE` by default) |

**Examples**

```excel
=HOLFIN.ECONINDICATOR("cpi", 2010, 2024, "table", "pct")
```

---

## Parameters Reference

### Period values

| Value | Description |
|---|---|
| `Annual` | Full fiscal year |
| `Quarterly` | Individual quarters |
| `TTM` | Trailing twelve months |

### Growth types

| Value | Description |
|---|---|
| `YoY` | Year-over-year change |
| `QoQ` | Quarter-over-quarter change |
| `CAGR3Y` | 3-year compound annual growth rate |
| `CAGR5Y` | 5-year compound annual growth rate |
| `CAGR10Y` | 10-year compound annual growth rate |

### View / mode values (Sectors, Market Data)

| Value | Description |
|---|---|
| `view: matrix` | Year × month/quarter grid (default) |
| `view: table` | Time series, one row per period |
| `mode: value` | Absolute value (default) |
| `mode: pct` | Percentage change vs. prior period |
| `mode: abs` | Absolute change vs. prior period |

---

## Need help?

- 💬 Support: [support@holfin.ai](mailto:support@holfin.ai)
- 🌐 Website: [holfin.ai](https://holfin.ai)
