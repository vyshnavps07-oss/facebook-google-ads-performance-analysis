# Facebook Ads vs. Google AdWords: Marketing Performance Analysis

An observational comparison of Facebook Ads and Google AdWords across reach, traffic, conversions, and cost efficiency, using Python. The project covers data-quality validation, KPI analysis, paired statistical testing, monthly trend analysis, and a proposed follow-up experiment.

**Headline result:** Facebook's aggregate cost per recorded conversion was **13.08 vs. 21.02** for AdWords (about 38% lower). The difference was statistically detectable on 658 matched dates (mean difference −8.50, 95% CI −9.52 to −7.48). Because the data is observational and appears simulated, this demonstrates analytical method rather than real channel performance. See [Dataset and data note](#dataset-and-data-note).

---

## Quick Links

| Resource | Link |
|---|---|
| Analysis notebook | [`campaign_analysis.ipynb`](campaign_analysis.ipynb) |
| Business case study (PDF memo) | [`Facebook_vs_Google_AdWords.pdf`](Facebook_vs_Google_AdWords.pdf) |
| Dataset (local copy) | [`dataset.csv`](dataset.csv) |
| Dataset (original source, Kaggle) | [A/B Testing Analysis: Facebook vs AdWord](https://www.kaggle.com/datasets/shubhamdamai/ab-testing-analysis-facebook-vs-adword) |
| Portfolio | [vyshnav-portfolio-woad.vercel.app](https://vyshnav-portfolio-woad.vercel.app/) |

---

## Study Design

This is an **observational comparison** of the supplied dataset, not a randomized A/B test. Results describe differences in recorded performance and do not show that either platform *caused* better outcomes.

## Dataset and Data Note

| Item | Detail |
|---|---|
| Records / columns | 1,000 records, 17 columns |
| Date range | 22 Dec 2021 to 20 Dec 2024 (658 distinct dates) |
| Repeated dates | 255 dates have multiple records; the record grain is not documented |
| Missing values / duplicates | None |
| Derived-column check | CTR and CVR columns recompute from raw counts with 0 mismatches |
| Invalid records | 10 Facebook records show conversions greater than clicks (retained and flagged) |
| Cost units | Currency is not specified; values are reported in the dataset's original units |

**Simulated-data note:** Every metric is consistent with uniform random generation, and funnel metrics are essentially uncorrelated (views vs. clicks and clicks vs. conversions both r ≈ 0). Real campaign data normally shows strong relationships there. For that reason, the project reports comparisons between platforms but does not draw business conclusions from within-platform correlations.

---

## Key Findings

KPIs use aggregate totals (total numerator ÷ total denominator), not averages of row-level ratios.

| Metric | Facebook Ads | Google AdWords | Advantage |
|---|---:|---:|---|
| Views | 2,152,031 | 4,771,438 | AdWords |
| Clicks | 44,196 | 60,128 | AdWords |
| Recorded conversions | 11,975 | 5,933 | Facebook |
| Recorded cost | 156,610 | 124,741 | AdWords (lower total) |
| Click-through rate (CTR) | 2.05% | 1.26% | Facebook |
| Conversion rate (CVR) | 27.10% | 9.87% | Facebook |
| Cost per click (CPC) | 3.54 | 2.07 | AdWords |
| Cost per 1,000 views (CPM) | 72.77 | 26.14 | AdWords |
| **Cost per acquisition (CPA)** | **13.08** | **21.02** | **Facebook** |

- Facebook recorded about **102% more conversions** and an aggregate CPA about **38% lower**.
- AdWords delivered about **2.2× the views** and more clicks, at a CPC about 41% lower and a CPM about 64% lower.
- The pattern held in **all 37 months**: Facebook led on conversions, CTR, CVR, and CPA; AdWords led on views, clicks, and CPC.
- **Robustness:** excluding the 10 invalid Facebook records moves Facebook CPA from 13.08 to 13.13, so the conclusion does not depend on them.

Traffic volume is not the same as conversion outcome: AdWords produced more clicks but fewer than half as many conversions.

## Statistical Results

Records were aggregated by date, then compared across the 658 matched dates with paired t-tests and Wilcoxon signed-rank tests.

| Metric | Mean difference (Facebook − AdWords) | 95% CI | Cohen's dz | Paired t-test | Wilcoxon |
|---|---:|---:|---:|---|---|
| CTR (percentage points) | 0.94 | 0.85 to 1.02 | 0.85 | p < 0.001 | p < 0.001 |
| CVR (percentage points) | 21.41 | 19.96 to 22.86 | 1.13 | p < 0.001 | p < 0.001 |
| CPC | 2.00 | 1.80 to 2.20 | 0.76 | p < 0.001 | p < 0.001 |
| **CPA** | **−8.50** | **−9.52 to −7.48** | **−0.64** | **p < 0.001** | **p < 0.001** |

A negative CPA difference means Facebook's date-level CPA was lower. Statistical significance here shows an association in the supplied data, not causation.

---

## Methodology

The notebook follows this workflow:

1. **Data acquisition and quality assessment**: dimensions, types, missing values, duplicates, date coverage, repeated dates, KPI-formula validation, conversions-vs-clicks consistency, IQR outlier review.
2. **Data preparation**: separate analytical copy, date features, anomaly flags (records retained, not altered).
3. **Exploratory data analysis**: descriptive statistics, distributions, correlations.
4. **Marketing KPI analysis**: views, clicks, conversions, CTR, CVR, CPC, CPM, CPA.
5. **Statistical analysis**: date-level aggregation, paired t-test, Wilcoxon test, effect sizes, confidence intervals.
6. **Time-based analysis**: monthly volume and monthly KPI trends.
7. **Insights and recommendations**.

## Repository Structure

```text
facebook-google-ads-performance-analysis/
├── campaign_analysis.ipynb          # Full analysis notebook
├── Facebook_vs_Google_AdWords.pdf   # Business case study / memo
├── dataset.csv                      # Local copy of the dataset
├── requirements.txt                 # Python dependencies
├── README.md
└── .gitignore
```

## How to Run

```bash
git clone https://github.com/vyshnavps07-oss/facebook-google-ads-performance-analysis.git
cd facebook-google-ads-performance-analysis

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

pip install -r requirements.txt
jupyter notebook campaign_analysis.ipynb
```

The notebook reads the local [`dataset.csv`](dataset.csv), so no Kaggle account or API credentials are needed. Run the cells in order.

---

## Recommendations

1. **Pilot Facebook for a conversion-focused objective.** Its lower recorded CPA and higher conversion volume make it the stronger candidate for a controlled test.
2. **Keep AdWords for reach and traffic objectives**, where it has lower CPC and CPM.
3. **Validate with a controlled experiment before any permanent budget shift**, using comparable audiences, conversion definitions, attribution windows, and periods, with randomized assignment or a holdout where feasible.
4. **Measure business outcomes, not platform metrics alone**: capture revenue and lead quality so ROAS and profitability can be assessed.

The proposed pilot design and decision thresholds are in the [case study PDF](Facebook_vs_Google_AdWords.pdf).



## Tech Stack

Python · Pandas · NumPy · SciPy · Matplotlib · Seaborn · Jupyter Notebook

## Author

**Vyshnav P S**: Data Analyst (Python, SQL, Power BI)
[Portfolio](https://vyshnav-portfolio-woad.vercel.app/) · [GitHub](https://github.com/vyshnavps07-oss)

---

*Self-directed portfolio case study using a publicly available dataset. Findings are limited to the fields and assumptions documented above.*
