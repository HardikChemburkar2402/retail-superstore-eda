# 🛒 Retail Superstore EDA — Uncovering the Discount Problem

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0-lightblue?style=flat-square)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Seaborn-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

## What This Project Is About

Four years of US retail transactions. $2.3M in revenue. 12.5% profit margin. And **1 in 5 orders losing money**.

This EDA investigates why — and finds a clear, quantifiable answer in the data.

## The Core Finding

Discounts above 20% are unprofitable. Always. Across 9,994 transactions, the correlation between discount rate and profit margin is **−0.86**. Orders with 40%+ discounts lose an average of $299 per transaction.

The business is writing cheques it doesn't need to write.

## Project Structure

```
retail-superstore-eda/
│
├── retail_eda.ipynb              # Main analysis notebook
├── report.md                     # Full written report with findings
├── Sample - Superstore.csv       # Dataset
│
├── charts/
│   ├── univariate_analysis.png
│   ├── bivariate_analysis.png
│   ├── timeseries_analysis.png
│   ├── correlation_analysis.png
│   ├── subcategory_analysis.png
│   └── business_insights.png
│
└── README.md
```

## Key Findings at a Glance

| Finding            | Detail                                                            |
| ------------------ | ----------------------------------------------------------------- |
| Discount threshold | Orders above 20% discount average a **loss**                      |
| Worst sub-category | Tables: −$17,725 on $206K revenue                                 |
| Best sub-category  | Copiers: $55,618 profit, low order volume                         |
| Category gap       | Technology earns 8× more profit than Furniture on similar revenue |
| Seasonality        | Q4 generates 2.4× more revenue than Q1                            |
| Growth trend       | Revenue growing but decelerating — 29% in 2016 → 20% in 2017      |
| Regional outlier   | Central region profit margin ~8% vs West at ~15%                  |

## Tools & Techniques

- **Data cleaning** — dtype conversion, feature engineering, outlier inspection
- **Univariate analysis** — distributions, value counts, frequency histograms
- **Bivariate analysis** — grouped aggregations, scatter plots, cross-category comparison
- **Time-series analysis** — monthly trends, seasonality decomposition, YoY growth
- **Correlation analysis** — heatmap, discount threshold identification
- **Sub-category deep dive** — bubble chart, horizontal bar, multi-dimensional comparison
- **Business insight narration** — findings written for a non-technical stakeholder audience

## How to Run

```bash
# Clone the repo
git clone https://github.com/yourusername/retail-superstore-eda.git
cd retail-superstore-eda

# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# Launch notebook
jupyter notebook retail_eda.ipynb
```

## Dataset

**Source:** [Superstore Dataset — Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)  
9,994 rows · 21 columns · US retail transactions 2014–2017

---

_Full methodology, limitations and next steps in [report.md](report.md)_
