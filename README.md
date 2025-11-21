# NVIDIA Stock Analysis & Valuation

**Comprehensive Time-Series Analysis • Technical Indicators • Forecasting • DCF Valuation • Sensitivity Analysis**

This project performs an end-to-end financial analysis of **NVIDIA Corporation (NVDA)** using historical market data, financial statements, volatility modeling, and multi-scenario valuation.
The goal is to understand NVDA’s price behavior, risk characteristics, operating performance, and intrinsic value under reasonable long-term assumptions.

---

### **Project Structure**

The analysis includes:

1. **Data Loading & Cleaning**
2. **Price Trend Visualization**
3. **Return & Volatility Analysis**
4. **Technical Indicators (SMA, RSI, MACD)**
5. **Trading Strategy Simulation**
6. **Fundamental Analysis (2019–2023 financial statements)**
7. **DCF Valuation (5-year FCFF forecast + terminal value)**
8. **WACC Estimation**
9. **Intrinsic Value per Share Calculation**
10. **Sensitivity Analysis (WACC & Terminal Growth)**

---

### **Data Coverage**

#### **1. Historical Stock Prices**

* **1999–2024** (from NVIDIA_stock_data.csv)
* Used for trend analysis, returns, and volatility models.

#### **2. Financial Statements (Input Data)**

Manually provided:

* **2019**
* **2020**
* **2021**
* **2022**
* **2023**

Used to compute revenue growth, margins, reinvestment ratios, etc.

#### **3. Forecast Period (DCF Model)**

* **2024–2028** (5-year FCFF projection)

---

#### 1. Price Trend Analysis

Historical closing prices were plotted to visualize long-term growth.
Key insight: massive acceleration post-2019 driven by AI/Data-center demand.


#### 2. Returns & Volatility Analysis

* Daily returns + log returns computed
* Plots show periods of extreme volatility during tech cycles and macro shocks
* 30-day rolling volatility highlights clustered volatility
* EWMA (λ=0.94) also used to model time-varying risk
  

#### 3. Technical Indicators Implemented

* Simple Moving Averages (SMA 20 & SMA 50) -> Common trend-following indicators.
* Relative Strength Index (RSI-14) -> Momentum and overbought/oversold signals.
* MACD -> Short-term vs long-term momentum comparison.

#### 4. Trading Strategy Backtest

A simple **SMA 20/50 crossover strategy**:

* **Buy** when SMA20 > SMA50
* **Sell** when SMA20 < SMA50

Strategy returns were compared against Buy-and-Hold.

Result: B&H outperforms SMA strategy historically due to NVDA's explosive long-term trend.


#### 5. Financial Statement Summary (2019–2023)

These were the basis for growth and margin assumptions:

| Metric                          | Value  |
| ------------------------------- | ------ |
| **Average Revenue Growth**      | ~58%   |
| **Average EBIT Margin**         | ~36.6% |
| **Approx Tax Rate**             | ~14.1% |
| **Depreciation / Revenue**      | ~9.1%  |
| **Capex / Revenue**             | ~–8.0% |
| **Δ Working Capital / Revenue** | ~–1.9% |

NVDA demonstrates extremely high growth and expanding profitability.


#### 6. FCFF Forecast (2024–2028)

Using realistic assumptions:

* **Revenue growth:** 20% annually
* **EBIT margin:** 32%
* **Tax rate:** 15%
* **Reinvestment ratios:**

  * Depreciation: 5% revenue
  * Capex: –6% revenue
  * Working capital: –1% revenue

Resulting FCFF (example):

| Year | FCFF (millions) |
| ---- | --------------- |
| 2024 | 48,668          |
| 2025 | 77,082          |
| 2026 | 122,086         |
| 2027 | 193,365         |
| 2028 | 306,259         |



#### 7. Discounted Cash Flow (DCF)

##### **Assumptions:**

* **Forecast Horizon:** 5 years
* **Terminal Growth (g):** 3%
* **WACC:** 10%

##### **Outputs:**

* **PV of FCFF (forecast period):** ≈ 657,051 million
* **PV of Terminal Value:** ≈ 2,838,964 million
* **Enterprise Value:** ≈ 3,320,023 million (≈ $3.32 trillion EV)

---

#### 8. Equity Value & Intrinsic Price

Using:

* NVDA’s debt
* cash
* shares outstanding

I compute:

```
Equity Value = EV – Debt + Cash
Intrinsic Value = Equity Value / Shares Outstanding
```

---

#### 9. Sensitivity Analysis

A **WACC × g** 2-way table was generated.

| g \ WACC  | 0.024    | 0.034  | 0.044 |
| --------- | -------- | ------ | ----- |
| **0.020** | 26,122   | 7,721  | 4,445 |
| **0.025** | –170,413 | 11,765 | 5,552 |
| **0.030** | –19,724  | 25,129 | 7,432 |

Interpretation:

* Small changes in assumptions → huge swings in valuation
* NVDA’s extreme growth makes DCF highly sensitive

---

#### 10. Included HTML Report

The full analysis is rendered in the file:

```
NVIDIA Stock Analysis.html
```

---

## Takeaways

* NVIDIA has **exceptional historical growth** driven by GPUs, AI, and data centers.
* **Returns and volatility** show high-risk, high-reward dynamics.
* **Technical indicators** confirm strong long-term uptrend.
* **DCF valuation is extremely sensitive**, especially given NVDA's explosive performance.
* Intrinsic value calculation needs careful handling of units (millions → dollars → shares).

