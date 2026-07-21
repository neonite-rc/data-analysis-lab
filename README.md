# Data Analysis Lab

Hands-on data analysis experiments with real-world datasets, SQL analytics, Python visualization, and end-to-end insight generation. Each project explores a different analytical technique or domain.

---

## Problem Statement

Business decisions are only as good as the data behind them. These projects answer real questions: Which customers are at risk of churning? What drives sales seasonality? How do we segment our market effectively?

---

## Project Table

| # | Project | Business Question | Key Insight |
|---|---------|-------------------|-------------|
| 01 | Sales Forecasting | What will sales look like next quarter? | Seasonality explains 60% of variance |
| 02 | Titanic Analysis | What factors increased survival chances? | Class and gender were stronger predictors than age |
| 03 | Customer Churn | Which customers are likely to leave? | RFM analysis beats raw churn probability |
| 04 | Global Temperature | Is climate change accelerating? | Warming rate doubled since 1980 |

---

## Approach + Why

| Technique | When to Use | Why |
|-----------|-------------|-----|
| **Cohort Analysis** | Customer behavior over time | Shows retention patterns, not just snapshots |
| **RFM Segmentation** | Identifying high-value customers | Simple, interpretable, actionable |
| **Time Series Decomposition** | Understanding seasonality | Separates trend, seasonality, noise |
| **A/B Testing** | Comparing interventions | Statistical rigor for decision-making |

---

## Key Insights

### Sales Forecasting
> Seasonality explains 60% of variance. Holiday promotions should start 3 weeks before peak.

### Customer Churn
> RFM analysis identified 15% of customers as "at-risk" who generated 40% of revenue. Retention focus should be here.

### Titanic Analysis
> Class and gender were stronger predictors than age. First-class women had 97% survival rate vs 16% for third-class men.

---

## SQL Highlights

```sql
-- RFM Segmentation
WITH rfm AS (
  SELECT
    customer_id,
    DATEDIFF(day, MAX(order_date), CURRENT_DATE) AS recency,
    COUNT(DISTINCT order_id) AS frequency,
    SUM(total_amount) AS monetary
  FROM orders
  GROUP BY customer_id
)
SELECT
  customer_id,
  NTILE(5) OVER (ORDER BY recency DESC) AS r_score,
  NTILE(5) OVER (ORDER BY frequency) AS f_score,
  NTILE(5) OVER (ORDER BY monetary) AS m_score
FROM rfm;
```

---

## What I Learned

1. **Data quality matters more than analysis technique** — Garbage in, garbage out
2. **Visualization reveals patterns** — Charts show what tables hide
3. **Simple models often beat complex ones** — RFM beats neural nets for segmentation
4. **Context is everything** — Statistical significance ≠ business significance
5. **Reproducibility builds trust** — Documented SQL beats undocumented analysis

---

## Stack

Python, pandas, SQL, matplotlib, seaborn, plotly, Jupyter

---

## Running Locally

```bash
# Clone
git clone https://github.com/neonite-rc/data-analysis-lab.git
cd data-analysis-lab

# Run a specific project
cd Sales_Forecasting
jupyter notebook
```

---

## License

MIT
