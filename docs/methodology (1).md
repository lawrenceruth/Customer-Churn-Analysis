# Methodology and Workbook Guide

Supporting detail for the [project README](../README.md).

## 1. Workbook map

| Tab | Purpose |
|---|---|
| `Data-Set` | Cleaned customer-level data (10,000 rows) |
| `KPIs` | KPI calculations feeding the dashboard cards |
| `Pivot-Table` | Churn rate by each dimension (age, products, card tier, satisfaction, geography, complaints, gender, activity, credit card) |
| `Pivot-Table-Analysis` | Total / churned / churn-rate tables per segment, each with a written business insight and recommendation |
| `Pivot-Chat` | Pivot charts used on the dashboard |
| `Interactive-Dashboard` | Final dashboard with KPI cards, charts and slicers |
| `Project Documentation` | Original in-workbook write-up (superseded by the README and this folder) |

## 2. Metric definitions

| Metric | Definition |
|---|---|
| Churn rate | Churned customers / total customers in the segment (`Exited = 1`) |
| Retention rate | 1 − churn rate (overall: 7,962 / 10,000 = 79.6%) |
| Share of churners | Segment churned customers / 2,038 |
| Share of base | Segment customers / 10,000 |

## 3. Data preparation

Checks performed before analysis:

- Missing values
- Duplicate `CustomerId` values
- Field consistency review
- Age grouped into four bands: 18–30, 31–45, 46–60, 61+
- Churn percentages calculated per segment

> **To complete:** record the *outcome* of each check (for example, "0 missing values, 0 duplicate IDs, N rows corrected"). A check without a reported result is not verifiable by a reader.

## 4. Dashboard features

- **Slicers:** the documentation lists Age Group, Satisfaction Score, Geography, Customer Complaints and Number of Products. The dashboard screenshot currently shows three (Geography, Customer Complaints, Age Group). Confirm which are actually connected.
- **KPI cards:** Total Customers (10,000), Churned (2,038), Retained (7,962), Customers with Complaints (2,044).
- **Charts:** churn rate by satisfaction score, geography, age band, number of products and complaint status.

## 5. Tools

Microsoft Excel, Pivot Tables, Pivot Charts, Slicers, Camera Tool (for KPI snapshots), Conditional Formatting, Excel formulas.

## 6. QA log: items to fix before publishing

| # | Issue | Where | Fix |
|---|---|---|---|
| 1 | Grand Totals on rate pivots sum the rates (99.2%, 218.0%, 81.5%, 101.9%, 65.3%, 99.6%, 41.5%, 41.1%, 41.0%) | `Pivot-Table` | Remove Grand Totals, or compute the rate as a calculated field (churned / total) |
| 2 | The "Customer Complaints" KPI card shows 99.5% labelled "Churn Rate", which is easy to misread as the overall rate | Dashboard | Relabel as "Churn rate among complainants" |
| 3 | Typos: "Compaints", "4 Produc", "Retaintion Rate", "Geograph Analysis Table" | Dashboard, pivots | Correct labels |
| 4 | Workbook title shows "(Recovered)" and "Back-Up" | File name | Save a clean, final-named copy |
| 5 | No-complaint churn displays as 0.1% (4 / 7,956 = 0.05%) | Dashboard | Show two decimals for this value |
| 6 | Findings in the in-workbook documentation use "significantly" without a statistical test | Documentation | Use "materially higher" or run a test |
| 7 | Recommendation to "encourage customers to adopt additional products" conflicts with 82.7–100% churn at 3–4 products | Documentation | Replaced in README with an audit-first approach |

## 7. Limitations

- Descriptive, single-variable analysis. No multivariate control for overlapping segments.
- No significance testing.
- Complaint flag may reflect post-exit logging (possible target leakage). Verify against source timestamps.
- The 3-product (n = 266) and 4-product (n = 60) groups are small.
