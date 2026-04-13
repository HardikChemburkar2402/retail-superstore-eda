# Retail Superstore Sales — Exploratory Data Analysis

**Author:** Hardik Chemburkar
**Domain:** Retail & Sales Analytics  
**Tools:** Python · Pandas · Matplotlib · Seaborn · NumPy  
**Dataset:** Sample Superstore Sales Dataset (Kaggle) — 9,994 transactions, 2014–2017

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Dataset Description](#2-dataset-description)
3. [Methodology](#3-methodology)
4. [Executive Summary](#4-executive-summary)
5. [Key Findings](#5-key-findings)
6. [Business Recommendations](#6-business-recommendations)
7. [Limitations](#7-limitations)
8. [Next Steps](#8-next-steps)

---

## 1. Project Overview

This project performs a comprehensive exploratory data analysis on four years of retail transaction data from a US-based superstore. The objective is to move beyond surface-level reporting and identify the structural drivers of profitability — and loss — across products, regions, customer segments and time periods.

The central question this analysis answers:

> **Why is an $2.3M revenue business operating at only 12.5% profit margin, with nearly 1 in 5 orders losing money?**

The answer, as this analysis demonstrates, is a discounting problem — systematic, measurable and fixable.

---

## 2. Dataset Description

| Attribute      | Detail                               |
| -------------- | ------------------------------------ |
| Source         | Kaggle — Superstore Sales Dataset    |
| Time Period    | January 2014 – December 2017         |
| Total Rows     | 9,994                                |
| Total Columns  | 21 (+ 6 engineered features)         |
| Geography      | United States (4 Regions, 49 States) |
| Missing Values | None                                 |
| Duplicate Rows | None                                 |

**Key columns used:**

- `Sales`, `Profit`, `Discount`, `Quantity` — core financial metrics
- `Category`, `Sub-Category` — product hierarchy
- `Region`, `Segment` — business dimensions
- `Order Date`, `Ship Date` — temporal features

**Engineered features added:**

- `Order Year`, `Order Month`, `Order Quarter` — for time-series analysis
- `Ship Days` — delivery duration (Ship Date − Order Date)
- `Profit Margin %` — profit as a percentage of sales per transaction
- `Discount Bucket` — discount grouped into 7 bands for threshold analysis

---

## 3. Methodology

The analysis follows a structured EDA pipeline:

```
Raw CSV → Data Cleaning → Feature Engineering → Univariate Analysis
→ Bivariate Analysis → Time-Series Trends → Correlation Analysis
→ Sub-Category Deep Dive → Business Insights → Recommendations
```

All visualisations were built using Matplotlib and Seaborn with a consistent styling configuration. Charts were designed to be self-explanatory — a business stakeholder with no data background should be able to read each chart without a legend explanation.

---

## 4. Executive Summary

| Metric                        | Value             |
| ----------------------------- | ----------------- |
| Total Revenue (2014–2017)     | $2,297,201        |
| Total Profit                  | $286,397          |
| Overall Profit Margin         | 12.5%             |
| Total Orders                  | 5,009             |
| Loss-Making Orders            | 1,871 (18.7%)     |
| Average Discount Applied      | 15.6%             |
| Average Shipping Duration     | 4.0 days          |
| Most Profitable Sub-Category  | Copiers ($55,618) |
| Least Profitable Sub-Category | Tables (−$17,725) |
| Best Region by Profit         | West ($108,418)   |
| Worst Region by Profit        | Central ($39,706) |

**The headline number that demands attention: 18.7% of all orders are loss-making.** That is not a rounding error or an accounting quirk — it represents 1,871 transactions where the business actively lost money. Across $2.3M in revenue, the profit margin should be substantially higher than 12.5%. The analysis identifies exactly where and why this is happening.

---

## 5. Key Findings

### Finding 1 — Discounting Above 20% Destroys Profitability

This is the single most important finding in the analysis.

Average profit per order by discount level:

| Discount Range | Avg Profit per Order |
| -------------- | -------------------- |
| 0%             | +$67                 |
| 1–10%          | +$96                 |
| 11–20%         | +$25                 |
| 21–30%         | **−$46**             |
| 31–40%         | **−$109**            |
| 41–50%         | **−$299**            |
| 50%+           | **−$89**             |

The breakeven threshold is approximately 20–21% discount. Every order above this threshold is, on average, a loss-making transaction. The correlation between Discount and Profit Margin is **−0.86** — one of the strongest negative relationships possible in a real-world dataset.

---

### Finding 2 — Furniture Is a Structurally Unprofitable Category

Furniture generates $740K in revenue — comparable to Technology at $840K — but produces only $18.5K in profit versus Technology's $145.5K. That is an 8× gap in profitability on similar revenue.

The root cause is two specific sub-categories:

| Sub-Category | Total Sales | Total Profit | Avg Discount |
| ------------ | ----------- | ------------ | ------------ |
| Tables       | $206K       | **−$17,725** | 26%          |
| Bookcases    | $114K       | **−$3,500**  | 21%          |

Both are above the 20% discount threshold. Tables alone loses $17,725 — wiping out the profits of several smaller but healthy sub-categories. 33.7% of all Furniture orders are loss-making, compared to 14.7% for Technology and Office Supplies.

---

### Finding 3 — The Central Region Has a Profitability Problem

Central generates $500K in sales — more than South — but only $39.7K in profit. West generates $730K in sales and $108.4K in profit. The Central region's profit-to-sales ratio is approximately 8%, compared to West's 15%. This warrants a region-specific pricing and discount policy review.

---

### Finding 4 — Strong Q4 Seasonality, Weak Q1

Average sales by quarter across all four years:

| Quarter      | Avg Sales |
| ------------ | --------- |
| Q1 (Jan–Mar) | $90K      |
| Q2 (Apr–Jun) | $111K     |
| Q3 (Jul–Sep) | $153K     |
| Q4 (Oct–Dec) | **$220K** |

Q4 generates **2.4× more revenue than Q1**. This is a consistent, repeatable pattern across all four years. The business should plan inventory, staffing and marketing spend accordingly rather than treating all quarters equally.

---

### Finding 5 — Growth Is Decelerating

| Year | Revenue | YoY Growth |
| ---- | ------- | ---------- |
| 2014 | $484K   | —          |
| 2015 | $471K   | −2.7%      |
| 2016 | $609K   | +29.3%     |
| 2017 | $733K   | +20.4%     |

2015 was a contraction year. 2016 saw a sharp recovery. 2017 growth, while strong at 20%, is decelerating from 2016's peak. If this trend continues, 2018 growth could be in single digits. The business needs to identify new growth drivers — new geographies, new product lines or improved retention — before the curve flattens.

---

### Finding 6 — Copiers Are the Highest-Value Hidden Opportunity

Copiers rank 10th in order volume but 1st in total profit at $55,618. They have a high average order value and are sold with an average discount of only 16% — below the danger threshold. Scaling Copier sales through targeted B2B outreach or corporate bundling could significantly improve overall margins without requiring any operational changes.

---

## 6. Business Recommendations

**1. Enforce a 20% discount ceiling immediately.**  
No discount above 20% should be applied without senior approval. The data shows this threshold clearly — it is not an estimate, it is derived from 9,994 transactions. Implementing this single policy change would eliminate the majority of loss-making orders.

**2. Conduct a Tables product line review.**  
Tables loses $17,725 on $206K in revenue. Before discontinuing, investigate whether the losses are driven entirely by discounting or also by high cost of goods and shipping. If the product is profitable at full price, the fix is discount policy. If it is structurally unprofitable, consider discontinuation or a price increase.

**3. Build a Central region discount audit.**  
Central's underperformance relative to West and East on profit margin suggests either local competitive pressure is forcing deeper discounts, or regional sales teams have more discount authority than they should. A transaction-level audit by sales rep would identify whether this is structural or behavioural.

**4. Plan resources around the Q4 peak and Q1 trough.**  
Inventory, marketing spend and staffing should reflect the 2.4× revenue difference between Q4 and Q1. Running Q1 campaigns with Q4 budget assumptions is a reliable way to erode margins on an already thin quarter.

**5. Prioritise Copier and Technology sales in B2B channels.**  
Technology accounts for the highest revenue and highest profit. Copiers specifically have an exceptional profit-per-order ratio. A targeted corporate sales motion focused on Technology products, particularly Copiers and Phones, would improve overall portfolio margins.

---

## 7. Limitations

- **No customer-level data.** This dataset contains order-level data only. There is no way to calculate customer lifetime value, repeat purchase rate or churn — all of which are essential for a complete business picture.
- **No cost breakdown.** Profit figures are taken as given. Without knowing the split between cost of goods, shipping cost and operational overhead, it is not possible to attribute losses precisely.
- **US market only.** All observations are from a single country. Findings are not generalisable beyond this geography.
- **Static dataset.** The data ends in December 2017. Any recommendations should be validated against more recent data before implementation.
- **Correlation ≠ Causation.** The strong relationship between discount and profit loss is compelling, but this is observational data. A controlled pricing experiment would be required to confirm causality.

---

## 8. Next Steps

The natural progression from this EDA is:

1. **Customer Segmentation (Clustering)** — use RFM (Recency, Frequency, Monetary) analysis to identify high-value customer segments worth protecting and growing.
2. **Sales Forecasting** — build a time-series forecasting model (ARIMA or Prophet) on monthly sales to project 2018 revenue by category and region.
3. **Profitability Prediction Model** — train a classification model to predict whether a given order will be loss-making at the time of order creation, enabling real-time discount alerts for the sales team.
4. **Discount Optimisation** — build a regression model that identifies the optimal discount level per sub-category that maximises revenue without crossing into loss territory.

---

_Analysis performed in Python 3. Full code available in `retail_eda.ipynb`. All charts saved as high-resolution PNG files in the repository._
