# 🛍️ Customer Behavior Analysis

A full end-to-end data analysis project covering data cleaning, SQL analysis, and interactive Power BI dashboards — built on a retail customer shopping dataset of **3,900 customers** generating **$233K in total revenue**.

---

## 📁 Project Structure

```
customer-behavior-analysis/
│
├── busines_insights.ipynb        # Python: data cleaning & preprocessing
├── sqlfile.sql                   # SQL: business queries & segmentation
├── customer_behaviour.pdf        # Power BI: multi-page interactive dashboard
└── README.md
```

---

## 🔧 Tools & Technologies

| Layer | Tool |
|---|---|
| Data Cleaning | Python (Pandas, SQLAlchemy) |
| Database | PostgreSQL |
| Business Analysis | SQL (Window Functions, CTEs, Aggregations) |
| Visualization | Power BI Desktop |
| Notebook | Jupyter Notebook |

---

## 🧹 Data Cleaning — `busines_insights.ipynb`

Performed in Python/Pandas before loading into PostgreSQL:

- **Missing value imputation** — filled null `Review Rating` values using **category-wise median** to preserve distribution integrity
- **Redundant column removal** — identified `Promo Code Used` and `Discount Applied` as identical via cross-tabulation; dropped the duplicate
- **Column normalization** — standardized all column names to `snake_case` for SQL compatibility
- **Feature engineering:**
  - `age_group` — segmented customers into `young adult`, `adult`, `middle aged`, `senior` via `pd.qcut()`
  - `purchase_frequency_days` — mapped text frequency labels (e.g., `Fortnightly`, `Quarterly`) to numeric day values
- **Database export** — loaded cleaned DataFrame into PostgreSQL via `SQLAlchemy` using `to_sql()`

---

## 🗄️ SQL Analysis — `sqlfile.sql`

Ten business questions answered using PostgreSQL:

| # | Question | Technique |
|---|---|---|
| 1 | Revenue by gender | `GROUP BY` + `SUM` |
| 2 | Discount users above average spend | Correlated subquery |
| 3 | Top 5 products by review rating | `ORDER BY` + `LIMIT` |
| 4 | Standard vs Express shipping spend | Conditional `WHERE` + `AVG` |
| 5 | Subscriber vs non-subscriber revenue | `GROUP BY` + `AVG` + `SUM` |
| 6 | Products with highest discount rate | `CASE WHEN` percentage formula |
| 7 | Customer segmentation (new/returning/loyal) | CTE + `CASE WHEN` |
| 8 | Top 3 products per category | CTE + `ROW_NUMBER()` window function |
| 9 | Repeat buyers vs subscription correlation | Filtered `GROUP BY` |
| 10 | Revenue by age group | `GROUP BY` + `SUM` |

---

## 📊 Power BI Dashboard — `customer_behaviour.pdf`

A four-page interactive dashboard with slicers for Gender, Subscription Status, Payment Method, Age Group, and Category.

### Page 1 — Executive Overview
- **KPIs:** $233.08K total revenue · 3.9K customers · 3.75 avg rating · 27% subscribed
- Revenue by season, category, and US state
- Subscription split: 73% unsubscribed vs 27% subscribed

### Page 2 — Customer Segmentation
- Revenue by age group (Young Adults lead at $62.14K)
- Purchase frequency distribution (Quarterly & Bi-Weekly dominate)
- Loyalty segments: Regular, Loyalists, Occasional, VIP, Infrequent
- Customer Lifetime Value scatter by subscription status

### Page 3 — Product & Discount Analysis
- Top 5 products by revenue (Blouse, Shirt, Dress, Pants, Jewelry — each ~$10K)
- Discount sensitivity: Clothing and Accessories show highest promo-driven purchases
- Age-wise discount uptake (~43–44% across all groups)
- Seasonal demand trends by category

### Page 4 — Location & Payment Intelligence
- Top revenue states: Montana ($5.78K), Illinois ($5.62K), California ($5.61K)
- Payment method split: nearly balanced across 6 methods; Credit Card leads at $40.31K
- Geographic customer density map across the US

---

## 💡 Key Business Insights

- **Clothing** is the highest-revenue category at ~$104K but has the lowest average review rating (3.72), signaling a potential quality or satisfaction gap
- **Fall** drives peak seasonal revenue — ideal for targeted promotional campaigns
- With **73% unsubscribed**, there is significant headroom for loyalty program growth
- **Young adults** represent the highest-value customer segment by revenue
- **Credit Card and PayPal** together account for the largest payment revenue share
- Repeat buyers (5+ purchases) correlate strongly with subscription status

---

## 🚀 Getting Started

### Prerequisites
```
Python 3.8+
PostgreSQL
Jupyter Notebook
Power BI Desktop
```

### Run the Notebook
```bash
git clone https://github.com/your-username/customer-behavior-analysis.git
cd customer-behavior-analysis
pip install pandas sqlalchemy psycopg2-binary jupysql
jupyter notebook busines_insights.ipynb
```

### Load SQL Queries
Connect to your PostgreSQL instance and run `sqlfile.sql` against the `customer_behaviour` database exported from the notebook.

---

## 📬 Connect

Built by **[Your Name]** · [LinkedIn](https://linkedin.com/in/yourprofile) · [Portfolio](https://yourportfolio.com)

> ⭐ Star this repo if you found it useful!
