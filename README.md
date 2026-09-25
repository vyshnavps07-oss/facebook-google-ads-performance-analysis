 # Strategic Ad Spend Optimization: Facebook vs. AdWords

## Project Overview

This project analyzes the performance of marketing campaigns across Facebook and Google AdWords to mathematically determine the optimal allocation of advertising budgets. By leveraging programmatic data ingestion, statistical hypothesis testing, and machine learning, this analysis transitions marketing strategy from intuition-based to data-driven.

## Data Source

* **Dataset:** [A/B Testing Analysis (Facebook vs. AdWord)](https://www.kaggle.com/datasets/shubhamdamai/ab-testing-analysis-facebook-vs-adword)
* **API:** Programmatically ingested via the Kaggle API.

## Tech Stack

* **Language:** Python
* **Libraries:** Pandas, NumPy (Data Manipulation) | SciPy, Statsmodels (Statistical Analysis) | Scikit-learn (Machine Learning) | Matplotlib, Seaborn (Data Visualization)

## Methodology

1. **Automated Data Ingestion & QA:** Built a secure pipeline to authenticate and download Kaggle data, followed by automated null/duplicate screening.
2. **Exploratory Data Analysis (EDA):** Visualized distributions of Conversion Volume and Cost Per Click (CPC) to identify baseline performance.
3. **Statistical Hypothesis Testing (A/B Testing):** Executed a Welch's Two-Sample T-Test to mathematically prove variance in conversion rates.
4. **Predictive Modeling:** Deployed a Linear Regression model to test the viability of forecasting conversions based on click volume.
5. **Cointegration Analysis:** Conducted time-series analysis to determine if both platforms share underlying macroeconomic volatility.

## Key Findings & Business Recommendations

* **Facebook Drives 2x Volume:** Facebook statistically outperforms AdWords (p < 0.05), generating an average of 11.97 daily conversions compared to 5.93. *Recommendation: Reallocate primary budget to Facebook while implementing automated CPC caps.*
* **Clicks are a Vanity Metric:** The regression model revealed zero linear correlation (R-squared: -0.0365) between clicks and conversions. *Recommendation: Abandon CPC as a predictive KPI and pivot entirely to Cost Per Acquisition (CPA).*
* **Shared Market Volatility:** Cointegration testing confirmed both platforms suffer simultaneous downturns. *Recommendation: Diversify marketing channels (e.g., SEO, Email) to hedge against seasonal market dips, as AdWords cannot act as a safety net for Facebook.*

## Author

* **Vyshnav P S**
