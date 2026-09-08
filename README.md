# NIFTY 50 Financial Data Analysis

## Overview

This project performs financial data analysis, forecasting, risk assessment, and statistical hypothesis testing on historical NIFTY 50 index data, completed as a four-week internship project.

- **Week 1:** Exploratory Data Analysis (EDA)
- **Week 2:** Financial Forecast Model
- **Week 3:** Risk Analysis
- **Week 4:** Hypothesis Testing

## Dataset

- **Dataset:** NIFTY 50 Historical Data
- **Source:** Kaggle
- **Analysis Period:** 17 September 2007 – 20 February 2026
- **Cleaned Observations:** 4,522
- **Columns:** 10

The original dataset filename indicates coverage from 1995, but valid observations in the selected NIFTY 50 file begin from 17 September 2007.

---

## Week 1 — Exploratory Data Analysis

This phase performs Exploratory Data Analysis (EDA) on historical NIFTY 50 index data.

The analysis focuses on understanding long-term price trends, daily returns, return distributions, cumulative growth, moving-average relationships, and market volatility.

## Analysis Performed

### 1. Data Cleaning
- Removed the metadata row present in the source CSV.
- Converted date values into datetime format.
- Converted numerical columns into appropriate numeric data types.
- Checked missing values and duplicates.

### 2. Data Quality Validation
The dataset was checked for:

- Invalid High < Low relationships
- High values below Open or Close
- Low values above Open or Close
- Negative trading volume
- Duplicate records

All logical validation checks returned zero violations.

### 3. Price Analysis
Analyzed the historical closing-price movement of the NIFTY 50 over the study period.

### 4. Daily Return Analysis
Analyzed:

- Daily return distribution
- Positive and negative trading days
- Maximum daily gain
- Maximum daily loss
- Large daily movements above +2% and below -2%

### 5. Return Distribution
Calculated:

- Mean return
- Standard deviation
- Skewness
- Excess kurtosis

A histogram was also used to visualize the distribution of daily returns.

### 6. Cumulative Return
Calculated compounded cumulative price return using daily returns.

A hypothetical ₹100 investment model was also created to visualize the theoretical growth of the index price return.

### 7. Moving Average Analysis
Compared:

- 50-day Moving Average (MA50)
- 200-day Moving Average (MA200)

The relationship between the two moving averages was analyzed to understand longer-term trend changes.

### 8. Volatility Analysis
Calculated 30-day rolling standard deviation of daily returns to study changing market volatility.

Yearly average rolling volatility was also calculated and ranked.

## Key Findings

- The cleaned dataset contains **4,522 daily observations**.
- Daily returns averaged approximately **+0.0469%**.
- The maximum daily gain was **+17.74%** on 18 May 2009.
- The minimum daily return was **-12.98%** on 23 March 2020.
- Compounded cumulative price return over the analyzed period was approximately **+468.93%**.
- A theoretical ₹100 principal grew to approximately **₹568.93** based on compounded index price returns.
- MA50 was above MA200 on **3,062 of 4,323 valid observations (70.83%)**.
- Average 30-day rolling volatility was approximately **1.10%**.
- Maximum 30-day rolling volatility was approximately **4.84%**, observed on 24 November 2008.
- 2008 recorded the highest yearly average 30-day rolling volatility at approximately **2.61%**.

---

## Week 2 — Financial Forecast Model

This phase develops a basic financial forecast model for the NIFTY 50 closing price using lag-based features and Linear Regression.

### Forecasting Approach

- **Indicator:** NIFTY 50 Closing Price
- **Features:** 7 lag-based features (Close_Lag_1, Close_Lag_5, Close_Lag_10, Close_Lag_20, MA_5, MA_20, Daily_Return_Pct)
- **Model:** Linear Regression
- **Train/Test Split:** Chronological 80/20 split (no random shuffling)
- **Training Period:** 2007-10-16 to 2022-06-29 (3,601 samples)
- **Testing Period:** 2022-06-30 to 2026-02-20 (901 samples)

### Model Evaluation (Test Set)

| Metric | Value |
|--------|-------|
| MAE | 82.01 |
| RMSE | 114.23 |
| MAPE | 0.3747% |
| R² | 0.998622 |

### Future Forecast

- **Horizon:** 30 trading sessions (2026-02-23 to 2026-04-03)
- **Last Observed Close:** ₹25,571.25
- **First Forecast:** ₹25,614.96
- **Last Forecast:** ₹25,756.65
- **Forecast Change:** ₹185.40 (+0.7250%)
- **Direction:** Modest upward trajectory

### Week 2 Deliverables

- Jupyter notebook with complete implementation and executed outputs
- Actual vs Predicted visualization
- Future 30-session forecast visualization
- Professional DOCX report with analysis and interpretation

---

## Week 3 — Risk Analysis

This phase conducts a structured financial risk analysis of the NIFTY 50 index using historical data from 2007 to 2026.

### Risk Categories Analyzed

- **Market / Price Risk:** Price extremes, major declines, maximum drawdown
- **Volatility Risk:** Rolling 30-day volatility, yearly comparisons, high-volatility periods
- **Extreme Return / Shock Risk:** Single-day moves, frequency of ±2% days, return distribution (kurtosis)
- **Downside Risk:** Negative return frequency, Value at Risk (VaR), Conditional VaR (CVaR)
- **Drawdown Risk:** Peak-to-trough analysis, maximum drawdown, recovery time

### Key Risk Metrics

| Metric | Value |
|--------|-------|
| Maximum Drawdown | -59.86% (2008 crisis) |
| Worst Single-Day Loss | -12.98% (2020-03-23) |
| Best Single-Day Gain | +17.74% (2009-05-18) |
| Average 30-day Volatility | 1.10% |
| Peak Volatility | 4.84% (2008-11-24) |
| VaR (95% confidence) | -1.83% daily |
| CVaR (95% confidence) | -3.04% daily |
| Kurtosis | 16.07 (fat-tailed) |
| Extreme Days (±2%) | 387 (8.56%) |
| Negative Trading Days | 46.85% |

### Risk Severity Ranking

1. Market / Price Risk — Very High
2. Drawdown Risk — Very High
3. Volatility Risk — High
4. Extreme Return / Shock Risk — High
5. Downside Risk — Moderate

### Week 3 Deliverables

- Jupyter notebook with complete risk analysis and executed outputs
- Historical drawdown visualization
- Volatility risk visualization
- Extreme returns distribution chart
- Downside risk analysis chart
- Market risk overview chart
- Professional DOCX risk analysis report

---

## Week 4 — Hypothesis Testing

This phase conducts a statistically rigorous hypothesis test on the daily return series of the NIFTY 50 index to evaluate long-term return drift.

### Core Research Question

> *"Is the average daily return of the NIFTY 50 index significantly different from zero over the analyzed period (2007–2026)?"*

### Hypotheses Formulation

- **Null Hypothesis ($H_0$):** $\mu = 0$ (The mean daily return equals zero)
- **Alternative Hypothesis ($H_1$):** $\mu \neq 0$ (The mean daily return does not equal zero)
- **Significance Level ($\alpha$):** 0.05 (95% confidence level)

### Key Descriptive Statistics (Daily Returns)

| Metric | Value |
|--------|-------|
| Cleaned Dataset Observations | 4,522 |
| Valid Return Observations ($n$) | 4,521 |
| Missing Return Rows Removed | 1 |
| Mean Daily Return ($\mu$) | **+0.046935%** |
| Median Daily Return | **+0.062461%** |
| Standard Deviation ($s$) | **1.301451%** |
| Minimum Daily Return | **-12.980466%** |
| Maximum Daily Return | **+17.744066%** |

### Statistical Test Results

| Test Name | Null Hypothesis ($H_0$) | Test Statistic | p-Value | 95% Confidence Interval | Statistical Decision |
|-----------|-----------------------|----------------|---------|-------------------------|----------------------|
| **One-Sample t-Test (Primary)** | $\mu = 0$ | $t = 2.424855$ | **0.015353** ($p < 0.05$) | [+0.008988%, +0.084882%] | **Reject $H_0$** |
| **Wilcoxon Signed-Rank Test (Robustness)** | Median = 0 | $W = 4,748,216.0$ | **0.000054** ($p < 0.05$) | N/A (Non-parametric) | **Reject $H_0$** |

### Key Conclusions & Interpretation

- **Decision:** **Reject the Null Hypothesis ($H_0$)** since $p = 0.015353 < 0.05$.
- **Interpretation:** There is statistically significant evidence that the mean daily return of the NIFTY 50 index is positive (+0.0469%/day).
- **Economic Significance vs. Predictability:** While a +0.0469%/day drift compounds to an annualized return of ~12.5%, daily volatility ($s = 1.3015\%$) is **27.7 times larger** than the mean return. Thus, statistical significance does not imply short-term trade predictability.

### Week 4 Deliverables

- Fully executed Jupyter notebook: `NIFTY50_Week4_Hypothesis_Testing.ipynb`
- Daily return distribution chart: `assets/week4_return_distribution.png`
- Professional Word report: `NIFTY50_Week4_Hypothesis_Testing_Report.docx` (in root and `Report/`)

---

## Project Structure

```text
nifty50-financial-data-analysis/
│
├── assets/
│   ├── closing_price_trend.png
│   ├── daily_returns.png
│   ├── hypothetical_100_growth.png
│   ├── moving_averages.png
│   ├── return_distribution_histogram.png
│   ├── rolling_volatility_30d.png
│   ├── top_5_volatile_years.png
│   ├── trading_volume.png
│   ├── week2_actual_vs_predicted.png
│   ├── week2_future_forecast.png
│   ├── week3_drawdown.png
│   ├── week3_extreme_returns.png
│   ├── week3_market_risk.png
│   ├── week3_volatility.png
│   ├── week3_downside_risk.png
│   └── week4_return_distribution.png
│
├── DataSet/
│   └── NIFTY50_1995_to_Feb_2026.csv
│
├── Report/
│   ├── NIFTY50_Week1_Final_Report.docx
│   ├── NIFTY50_Week2_Financial_Forecast_Report.docx
│   ├── NIFTY50_Week3_Risk_Analysis_Report.docx
│   └── NIFTY50_Week4_Hypothesis_Testing_Report.docx
│
├── NIFTY50_Financial_Data_Analysis.ipynb          # Week 1 notebook
├── NIFTY50_Week1_Analysis_Report.docx              # Week 1 report
├── NIFTY50_Week2_Financial_Forecast.ipynb          # Week 2 notebook
├── NIFTY50_Week2_Financial_Forecast_Report.docx     # Week 2 report
├── NIFTY50_Week3_Risk_Analysis.ipynb               # Week 3 notebook
├── NIFTY50_Week3_Risk_Analysis_Report.docx          # Week 3 report
├── NIFTY50_Week4_Hypothesis_Testing.ipynb          # Week 4 notebook
├── NIFTY50_Week4_Hypothesis_Testing_Report.docx     # Week 4 report
├── README.md
└── .gitignore
```