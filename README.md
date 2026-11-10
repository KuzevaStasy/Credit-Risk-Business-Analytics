# 📊 Credit Risk Portfolio Analytics & Management Framework

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/pandas-2.0%2B-150458.svg)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.13%2B-4c72b0.svg)](https://seaborn.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Lab-orange.svg)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> A management-oriented credit analytics and early warning monitoring framework for consumer lending portfolios, translating granular loan application data into executive policy decisions and risk steering strategies.

---

## 🎯 Executive Overview

This repository demonstrates how a **Business Analytics & Credit Risk** function drives portfolio steering, risk monitoring, and governance in a non-banking financial institution (NBFI). 

Rather than focusing on black-box predictive modeling, the analysis emphasizes:
- **Baseline Portfolio Health:** Establishing reference risk rates and affordability benchmarks.
- **Risk Concentration & Exposure:** Identifying where aggregate loan losses cluster across ticket sizes.
- **Early Warning Indicators (EWIs):** Proactively detecting risk drift before delinquency materializes.
- **Actionable Governance:** Translating analytical findings into credit limit caps, pricing tiers, and underwriting cut-offs.

---

## 🗂️ Analytical Workflow & Notebook Structure

The project follows an end-to-end management reporting lifecycle structured across 4 sequential notebooks:

```text
Credit-Risk-Business-Analytics/
├── archive/
│   ├── README.md                                # Where to download the dataset
│   └── feature_matrix.csv                       # Consolidated feature matrix (not in the repo, gitignored)
├── reports/figures/                             # Figures used in this README
├── notebooks/
│   ├── 01_business_context_and_data_overview.ipynb        # Portfolio baseline KPIs & exposure distributions
│   ├── 02_portfolio_kpis_and_segmentation.ipynb           # Multi-dimensional risk segmentation (Credit, Income, Bureau)
│   ├── 03_credit_risk_and_early_warning_indicators.ipynb  # 4-Pillar Early Warning Indicator (EWI) dashboard
│   └── 04_management_insights_and_reporting.ipynb         # Executive decision matrices & policy recommendations
├── requirements.txt                             # Python dependencies
├── LICENSE
└── README.md
```

### Module Breakdown

1. **`01_business_context_and_data_overview.ipynb`**
   - Business positioning and exploration of consolidated consumer credit records.
   - Target hygiene (handling sentinel missing value codes like `-999`).
   - Baseline KPI definitions (analyzed volume, mean credit ticket, observed default baseline).

2. **`02_portfolio_kpis_and_segmentation.ipynb`**
   - Quantile segmentation across exposure (`AMT_CREDIT`), income tiers (`AMT_INCOME_TOTAL`), and demographics (`AGE_YEARS`).
   - Bureau score calibration using `EXT_SOURCE_2`.
   - Multi-dimensional portfolio concentration analysis (Volume % vs. Exposure % vs. Default %).

3. **`03_credit_risk_and_early_warning_indicators.ipynb`**
   - Construction of a 4-pillar Early Warning Indicator (EWI) framework.
   - Calculation of risk spread metrics relative to portfolio baseline (8.06%).
   - Identification of adverse selection in lower income tiers and younger borrower cohorts.

4. **`04_management_insights_and_reporting.ipynb`**
   - Executive dashboard synthesis and risk-vs-exposure decile modeling.
   - Operational policy matrix assigning risk thresholds to specific business owners.
   - Portfolio steering framework balancing **Growth vs. Risk vs. Profitability**.

---
## 🖼️ Portfolio Visual Insights

<p align="center">
  <img src="reports/figures/ewi_dashboard.png" width="85%" alt="Early Warning Dashboard" />
  <br>
  <em>Figure 1: 4-Pillar Early Warning Indicator (EWI) Risk Dashboard vs. Portfolio Baseline (8.06%)</em>
</p>

<table width="100%">
  <tr>
    <td width="50%" align="center">
      <img src="reports/figures/credit_exposure.png" alt="Credit Exposure Distribution" />
      <br><strong>Figure 2:</strong> Credit Exposure & Demographics
    </td>
    <td width="50%" align="center">
      <img src="reports/figures/risk_vs_exposure.png" alt="Exposure vs Risk Deciles" />
      <br><strong>Figure 3:</strong> Exposure Concentration vs. Default Rate
    </td>
  </tr>
</table>

## 📈 Baseline Portfolio Snapshot

| Metric | Sample Portfolio Value | Management Description |
| :--- | :--- | :--- |
| **Analyzed Applications** | `100,000` | Full analyzed sample size |
| **Observed (Labeled) Loans** | `86,173` | Loans with a known outcome (the remaining 13,827 have no label) |
| **Portfolio Default Rate** | `8.06%` | Share of labeled loans with `TARGET = 1`; baseline risk benchmark |
| **Average Credit Exposure** | `$586,964.74` | Mean requested loan amount |
| **Average Annual Income** | `$170,680.03` | Borrower baseline affordability index |

---

## 🚦 Early Warning Indicator (EWI) Governance Matrix

| EWI Pillar | Highest-Risk Cohort | Observed Risk Rate | Spread vs. Baseline | Recommended Management Action |
| :--- | :--- | :--- | :--- | :--- |
| **EWI 1: Credit Size** | Quintile 3 "Medium" (avg. credit ~$499K) | 10.28% | `+2.22 pp` | Review pricing and limits for mid-sized loans; monitor the largest loans separately for exposure concentration |
| **EWI 2: Affordability** | Income quintile 3 "Medium" | 9.04% | `+0.98 pp` | Weak signal on its own; combine with bureau score and age before setting limits |
| **EWI 3: Demographics** | Young Applicants (<32 yrs) | 11.17% | `+3.11 pp` | Require employment proof / co-signers |
| **EWI 4: Bureau Score** | Score Quintile 1 (Lowest) | 15.20% | `+7.14 pp` | Implement hard automated underwriting cut-offs |

Default rates by credit size rise from 7.03% (smallest quintile) to 10.28% (middle quintile) and then fall to 5.92% (largest quintile), so risk frequency does not simply increase for small loans. The largest quintile still holds 38.9% of total exposure, which is why exposure is monitored separately.

---

## 🚀 Quickstart & Reproduction

### 1. Clone Repository & Setup Virtual Environment
```bash
git clone https://github.com/KuzevaStasy/Credit-Risk-Business-Analytics.git
cd Credit-Risk-Business-Analytics
# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Dataset Setup
Download the Home Credit feature matrix from Kaggle ([Home Credit Default Risk - Feature Tools](https://www.kaggle.com/datasets/willkoehrsen/home-credit-default-risk-feature-tools)) and place it in the `archive/` folder:
```text
archive/feature_matrix.csv
```
The notebooks read the first 100,000 rows and only eight columns (`SK_ID_CURR`, `TARGET`, `AMT_CREDIT`, `AMT_INCOME_TOTAL`, `DAYS_BIRTH`, `EXT_SOURCE_2`, `CNT_FAM_MEMBERS`, `REGION_RATING_CLIENT`). Run the notebooks in order (01 → 04).

### 3. Launch Notebooks
```bash
jupyter lab
```

---

## 🛠️ Tech Stack & Dependencies

- **Python 3.10+**
- **Data Wrangling:** `pandas >= 2.0.0`, `numpy >= 1.24.0`
- **Visualization:** `matplotlib >= 3.7.0`, `seaborn >= 0.13.0`
- **Interactive Environment:** `jupyterlab >= 4.0.0`

---

## ⚖️ Analytical Disclaimer

This project is built for business analytics demonstration and management decision simulation. `TARGET` is the binary payment-difficulty flag of the public Home Credit dataset (applications without an outcome are excluded), not the loss history of a live portfolio. All cutoff recommendations and thresholds should undergo vintage and loss forecasting validation prior to production deployment.

Amounts are shown with a `$` sign for readability; the dataset does not specify a currency. Results are based on the first 100,000 rows of the feature matrix, not a random sample.

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for details.
