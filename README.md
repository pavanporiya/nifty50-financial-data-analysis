# NIFTY 50 Financial Data Analysis

## Week 1 — Exploratory Data Analysis

This project performs Exploratory Data Analysis (EDA) on historical NIFTY 50 index data.

The analysis focuses on understanding long-term price trends, daily returns, return distributions, cumulative growth, moving-average relationships, and market volatility.

## Dataset

- **Dataset:** NIFTY 50 Historical Data
- **Source:** Kaggle
- **Analysis Period:** 17 September 2007 – 20 February 2026
- **Cleaned Observations:** 4,522
- **Columns:** 10

The original dataset filename indicates coverage from 1995, but valid observations in the selected NIFTY 50 file begin from 17 September 2007.

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
│   └── trading_volume.png
│
├── NIFTY50_Financial_Data_Analysis.ipynb
├── NIFTY50_Week1_Analysis_Report.docx
├── README.md
└── .gitignore
