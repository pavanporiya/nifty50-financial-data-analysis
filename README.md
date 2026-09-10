# NIFTY 50 Financial Data Analysis

## Overview

This project performs financial data analysis, forecasting, risk assessment, statistical hypothesis testing, data visualization, and final consolidated reporting on historical NIFTY 50 index data, completed as a six-week internship project.

- **Week 1:** Exploratory Data Analysis (EDA)
- **Week 2:** Financial Forecast Model
- **Week 3:** Risk Analysis
- **Week 4:** Hypothesis Testing
- **Week 5:** Data Visualization
- **Week 6:** Final Reporting & Presentation

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

## Week 5 — Data Visualization

This phase converts the analytical findings of Weeks 1–4 into presentation-ready visualizations. Every chart answers a specific financial question and is explained through its purpose, chart-type rationale, what it shows, financial interpretation, and key takeaway.

### Visualizations Created

| # | Visualization | Financial Question |
|---|---------------|--------------------|
| 1 | Long-term price trend | How has the NIFTY 50 closing price changed over 2007–2026? |
| 2 | Daily return behavior | How variable are daily returns, and when were the largest moves? |
| 3 | Return distribution | What shape do daily returns take (center, spread, tails)? |
| 4 | Moving averages (Close, MA50, MA200) | How do short-term and long-term trend measures relate? |
| 5 | Rolling 30-day volatility | When did market uncertainty increase? |
| 6 | Drawdown analysis | How severe and prolonged were declines from prior peaks? |
| 7 | Yearly performance (compounded) | How did calendar-year returns differ? |
| 8 | Volume analysis | How did trading volume vary over time? |
| A.1 | Monthly return heatmap | Is there recurring monthly return behavior? |
| A.2 | Volatility vs drawdown | Do high-volatility episodes align with deep drawdowns? |
| A.3 | Extreme return days | Which single days produced the largest gains and losses? |

### Coverage

- **Long-term price trend** — compounded price change of +468.93% (₹4,494.65 to ₹25,571.25), all-time closing high ₹26,328.55 (2 Jan 2026).
- **Daily return behavior** — noise-dominated daily moves with clusters of extreme days; best day +17.74% (18 May 2009), worst day -12.98% (23 Mar 2020).
- **Return distribution** — near-symmetric (skewness +0.06) but strongly fat-tailed (excess kurtosis +16.05).
- **Moving averages** — MA50 above MA200 on 70.83% of valid observations, inverting during the 2008 and 2020 crises.
- **Rolling volatility** — averaged 1.10%, peaked at 4.84% (24 Nov 2008), bottomed at 0.39% (Jul 2017).
- **Drawdown** — maximum drawdown -59.86% (trough 27 Oct 2008); deepest 2020 drawdown -38.44% (23 Mar 2020); 589 trading days in drawdown worse than -20%.
- **Yearly performance** — compounded calendar-year returns from -51.79% (2008) to +75.76% (2009); 16 of 20 years positive; partial years (2007, 2026) marked separately.
- **Volume analysis** — index-level volume; yearly median ≈0.19 M (2013–2019) vs ≈0.31 M (2020–2026); interpreted cautiously.
- **Cross-visualization insights** — volatility spikes coincide with drawdown episodes (correlation ≈ -0.74); fat tails visible in three independent charts; volume behaves as a coincident stress echo, not a leading indicator.

### Week 5 Deliverables

- Jupyter notebook: `NIFTY50_Week5_Data_Visualization.ipynb` (fully executed)
- 11 visualization images in `assets/week5/`
- Professional Word report: `reports/NIFTY50_Week5_Data_Visualization_Report.docx`

---

## Week 6 — Final Reporting

The final phase consolidates all five analytical stages into one coherent internship report. It is not a copy-paste of the previous deliverables: it re-derives the project's analytical story, connects findings across weeks, and adds forward-looking recommendations.

### Contents of the Final Report

- **Executive Summary** — the entire project on one page
- **Dataset Overview** — source, period, cleaning, and quality validation
- **Week 1–5 sections** — the objective, method, actual results, and interpretation of each stage
- **Integrated Findings Across the Project** — how EDA feeds risk analysis, how EDA structure shapes the forecast model, how risk metrics contextualize forecast error, how hypothesis testing adds inferential weight to the EDA, and how visualization verifies every claim
- **Key Findings** — the ten strongest findings with their results and significance
- **Analytical Insights** — cautious, evidence-based conclusions about the index's historical behavior
- **Recommendations for Future Analysis** — ten methodological next steps (multi-model comparison, exogenous variables, forecast intervals, walk-forward validation, GARCH volatility models, subsample testing, constituent-level analysis, regime detection, sensitivity analysis, regime-filter backtesting)
- **Limitations and Final Conclusion**
- **7 summary tables** (dataset, forecast evaluation, risk summary, hypothesis tests, key findings, recommendations, deliverables) and **8 selected figures** from Weeks 1–5 with numbered captions

All numbers in the final report were cross-checked against the executed Week 1–5 notebooks; no new analysis was performed and no previous result was altered.

### Week 6 Deliverables

- Final Word report: `Report/NIFTY50_Week6_Final_Report.docx`

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
│   ├── week4_return_distribution.png
│   │
│   └── week5/
│       ├── 01_long_term_price_trend.png
│       ├── 02_daily_return_behavior.png
│       ├── 03_return_distribution.png
│       ├── 04_moving_average_trend.png
│       ├── 05_rolling_volatility.png
│       ├── 06_drawdown_analysis.png
│       ├── 07_yearly_performance.png
│       ├── 08_volume_analysis.png
│       ├── 09_monthly_return_heatmap.png
│       ├── 10_volatility_vs_drawdown.png
│       └── 11_extreme_return_days.png
│
├── DataSet/
│   └── NIFTY50_1995_to_Feb_2026.csv
│
├── Report/
│   ├── NIFTY50_Week1_Final_Report.docx
│   ├── NIFTY50_Week2_Financial_Forecast_Report.docx
│   ├── NIFTY50_Week3_Risk_Analysis_Report.docx
│   ├── NIFTY50_Week4_Hypothesis_Testing_Report.docx
│   ├── NIFTY50_Week5_Data_Visualization_Report.docx
│   └── NIFTY50_Week6_Final_Report.docx
│
├── NIFTY50_Financial_Data_Analysis.ipynb          # Week 1 notebook
├── NIFTY50_Week2_Financial_Forecast.ipynb         # Week 2 notebook
├── NIFTY50_Week3_Risk_Analysis.ipynb              # Week 3 notebook
├── NIFTY50_Week4_Hypothesis_Testing.ipynb         # Week 4 notebook
├── NIFTY50_Week5_Data_Visualization.ipynb         # Week 5 notebook
├── README.md
└── .gitignore
```