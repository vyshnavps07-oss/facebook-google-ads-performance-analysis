# Facebook Ads vs. Google AdWords: Marketing Performance Analysis

A data analytics portfolio project comparing the recorded performance of
Facebook Ads and Google AdWords using Python. The analysis evaluates
reach, traffic, conversion activity, advertising cost efficiency, and
performance trends over time.

> **Study design:** This is an observational comparison of the supplied
> dataset, not a randomized A/B test. The results describe differences
> in recorded performance and should not be interpreted as proof that
> one platform caused better outcomes.

## Project Overview

The objective is to assess how the two advertising platforms performed
across key marketing funnel and cost-efficiency metrics, identify their
relative strengths, and develop practical recommendations for a
follow-up campaign test.

The analysis covers:

-   Data quality assessment and preparation
-   Exploratory data analysis (EDA)
-   Marketing KPI calculation and comparison
-   Date-level statistical testing
-   Monthly performance and cost trends
-   Business insights and recommendations

## Key Performance Findings

The following metrics are calculated from the full dataset using
aggregate totals.

  Metric                                  Facebook Ads   Google AdWords
  ------------------------------------- -------------- ----------------
  Views                                      2,152,031        4,771,438
  Clicks                                        44,196           60,128
  Recorded conversions                          11,975            5,933
  Recorded advertising cost                    156,610          124,741
  Click-through rate (CTR)                       2.05%            1.26%
  Conversion rate (CVR)                         27.10%            9.87%
  Cost per click (CPC)                            3.54             2.07
  Cost per thousand impressions (CPM)            72.77            26.14
  Cost per acquisition (CPA)                     13.08            21.02

### What the results indicate

-   **Facebook Ads recorded more conversions:** 11,975 compared with
    5,933 for Google AdWords.
-   **Facebook Ads had the lower aggregate CPA:** 13.08 compared with
    21.02, approximately 38% lower.
-   **Facebook Ads recorded higher CTR and CVR:** this indicates
    stronger recorded click-through and conversion efficiency in this
    dataset.
-   **Google AdWords generated greater reach and traffic:** it recorded
    approximately 2.2 times as many views and more clicks.
-   **Google AdWords had lower CPC and CPM:** it generated clicks and
    impressions at lower recorded unit costs.

**Overall interpretation:** Facebook Ads performed better on recorded
conversion volume and CPA, while Google AdWords performed better on
reach, traffic volume, CPC, and CPM. The preferred platform therefore
depends on the campaign objective. These results do not establish
profitability because revenue and profit data are not available.

## Statistical Analysis

A date-level comparison was conducted on **658 matched dates**. The
primary comparison focused on CPA, calculated after aggregating the
records by date and platform.

  Statistical measure                                         Result
  ------------------------------------------------- ----------------
  Mean CPA difference (Facebook − Google AdWords)              -8.50
  95% confidence interval                             -9.52 to -7.48
  Paired t-test                                           p \< 0.001
  Wilcoxon signed-rank test                               p \< 0.001

The negative mean difference indicates that Facebook Ads had a lower
date-level CPA on average in the matched-date comparison. Both tests
indicate a statistically significant difference under the analysis
assumptions.

**Interpretation caution:** Statistical significance does not establish
causality. The dataset is observational, the underlying record grain and
campaign assignment process are not documented, and the dates are
irregular. The tests should therefore be interpreted as evidence of an
association in the supplied data, not as proof that the platform itself
caused the observed difference.

## Analysis Workflow

1.  **Data acquisition** -- Loaded the supplied advertising dataset.
2.  **Data quality assessment** -- Checked dimensions, data types,
    missing values, duplicate records, date coverage, and potential data
    inconsistencies.
3.  **Data preparation** -- Parsed date fields, prepared analysis
    variables, and retained records while documenting relevant
    anomalies.
4.  **Exploratory data analysis** -- Examined distributions, summary
    statistics, outliers, and relationships between numerical variables.
5.  **KPI analysis** -- Compared views, clicks, conversions, CTR, CVR,
    CPC, CPM, and CPA.
6.  **Statistical analysis** -- Aggregated observations by date and
    applied paired t-tests and Wilcoxon signed-rank tests to matched
    dates.
7.  **Time-based analysis** -- Compared monthly reach, traffic,
    conversions, and cost-efficiency metrics.
8.  **Business recommendations** -- Summarized platform strengths and
    proposed a controlled follow-up test.

## Data Quality and Analytical Considerations

-   The dataset contains **1,000 records and 17 columns**.
-   The recorded date range is **22 December 2021 to 20 December 2024**.
-   There are **658 distinct dates**.
-   No missing values or exact duplicate rows were identified in the
    supplied dataset.
-   Multiple records occur on some dates. The underlying observation
    grain is not clearly documented; date-level analysis therefore uses
    aggregated values.
-   Ten Facebook Ads records have recorded conversions greater than
    clicks. These records were retained and flagged rather than
    automatically altered because the dataset does not provide enough
    information to determine whether they are invalid.
-   Outliers were reviewed in context rather than removed solely because
    they were statistically extreme.
-   Aggregate CTR, CVR, CPC, CPM, and CPA are calculated from the
    relevant total numerators and denominators, rather than by taking an
    unweighted average of row-level ratios.
-   The dataset does not specify the currency or unit for advertising
    cost. Cost values are therefore reported in the dataset's original
    units.
-   Revenue and profit fields are not available, so ROAS, ROI, and
    profitability cannot be calculated.

## Business Recommendations

1.  **Prioritize Facebook Ads for a conversion-focused test.** Its lower
    recorded CPA and higher recorded conversion volume make it the
    stronger candidate for a controlled conversion-efficiency pilot.
2.  **Retain Google AdWords for reach and traffic objectives.** Its
    higher views and clicks, together with lower CPC and CPM, indicate a
    different strength in the funnel.
3.  **Run a controlled follow-up experiment before making a permanent
    budget shift.** Use comparable audiences, conversion definitions,
    attribution windows, campaign periods, and measurement rules.
    Randomized audience assignment or a suitable holdout should be used
    where feasible.
4.  **Evaluate business outcomes, not platform metrics alone.** Capture
    revenue, lead quality, and downstream conversion outcomes to assess
    ROAS and profitability.
5.  **Monitor performance consistently.** Track CPA, conversion volume,
    CTR, CVR, CPC, and CPM using the same definitions across both
    platforms.

These recommendations are based on the supplied dataset and should be
validated with a properly designed campaign test.

## Tools and Technologies

-   **Python**
-   **Pandas** -- data manipulation and aggregation
-   **NumPy** -- numerical operations
-   **Matplotlib and Seaborn** -- data visualization
-   **SciPy** -- statistical testing
-   **Jupyter Notebook** -- analysis environment
-   **Kaggle API** -- dataset acquisition

## Repository Structure

``` text
marketing-ab-testing/
├── campaign_analysis.ipynb
├── A_B_testing_dataset.csv
├── README.md
└── Facebook_vs_Google_AdWords_Portfolio_Memo.docx
```

If the memo or dataset is stored in a different folder or is not
included in the public repository, update this tree to match the actual
repository contents before publishing.

## How to Run the Project

### 1. Clone the repository

``` bash
git clone https://github.com/vyshnavps07-oss/marketing-ab-testing.git
cd marketing-ab-testing
```

### 2. Create and activate a virtual environment (recommended)

``` bash
python -m venv .venv
```

Windows PowerShell:

``` powershell
.venv\Scripts\Activate.ps1
```

macOS/Linux:

``` bash
source .venv/bin/activate
```

### 3. Install dependencies

``` bash
pip install pandas numpy matplotlib seaborn scipy jupyter kaggle
```

### 4. Configure Kaggle access securely

If you download the dataset through the Kaggle API, configure your
Kaggle credentials locally using the official `kaggle.json` method or
environment variables. Do not place API usernames, keys, tokens, or
other secrets directly in the notebook or commit them to Git.

### 5. Run the notebook

``` bash
jupyter notebook campaign_analysis.ipynb
```

Run the notebook cells in order. If the CSV is already available in the
repository, configure the notebook to read the local file rather than
downloading it again.

## Limitations

-   The analysis is observational; no randomized experiment or audience
    assignment is documented.
-   The meaning of each row and the campaign-level structure are not
    fully specified.
-   The dates are irregular, and multiple records can occur on the same
    date.
-   The dataset does not document currency, attribution rules, audience
    characteristics, or campaign identifiers sufficiently to validate
    comparability.
-   Conversions exceeding clicks occur in ten Facebook Ads records;
    their validity cannot be established from the available fields.
-   Revenue, profit, and customer lifetime value are not provided.
    Profitability and ROAS cannot be assessed.
-   Other factors such as audience targeting, campaign objective,
    creative, bidding strategy, and platform attribution may influence
    the observed differences.

## Author

**Vyshnav P S**\
Data Analyst \| Python, SQL, Power BI & Data Analytics

------------------------------------------------------------------------

*This project is a self-directed portfolio case study using a publicly
available dataset. Findings are limited to the fields and assumptions
documented above.*
