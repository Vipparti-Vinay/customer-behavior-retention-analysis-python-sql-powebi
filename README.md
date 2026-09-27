# Decoding the shoppers: customer-behavior-retention-analysis-python-sql-powerbi

**Summary:** An end-to-end retail analytics project — from raw transactional data to an interactive 2-page Power BI dashboard — uncovering what drives customer spending, loyalty, and repeat purchases.

---

## Overview

This project analyzes 3,900 retail transactions to understand customer shopping behavior across demographics, product categories, discounts, and sales channels. It follows a complete data analyst workflow: data cleaning and feature engineering in Python, business-question analysis in SQL, and an interactive, drill-through-enabled dashboard in Power BI.

The project is based on Amlan Mohanty's Customer Behavior Data Analyst Portfolio Project tutorial, extended with additional EDA steps, 5 extra SQL business questions, and a fully redesigned, custom-themed 2-page dashboard including a drill-through "Deep Dive" page.

---

## Problem Statement

A retail company wants to better understand its customers' shopping behavior to improve sales, satisfaction, and long-term loyalty. Management has observed shifting purchase patterns across demographics, categories, and channels, and wants to know which factors — discounts, reviews, seasonality, or payment preference — actually drive purchase decisions and repeat business.

**Core question:** How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategy?

---

## Data Set

- **Source:** Retail customer transaction data
- **Size:** 3,900 rows × 18 columns
- **Key fields:**
  - Demographics: `age`, `gender`, `location`, `subscription_status`
  - Purchase details: `item_purchased`, `category`, `purchase_amount`, `season`, `size`, `color`
  - Behavior: `discount_applied`, `previous_purchases`, `frequency_of_purchases`, `review_rating`, `shipping_type`, `payment_method`
- **Data quality note:** 37 missing values in `review_rating`, imputed using the median rating per product category.

---

## Tools and Technologies

- **Python** (Pandas, Matplotlib, Seaborn) — data cleaning, feature engineering, EDA
- **PostgreSQL** — structured business-question analysis via SQL
- **Power BI** — interactive dashboard and DAX measures
- **Jupyter Notebook** — analysis environment
- **pgAdmin** — database management and CSV import
- **Git & GitHub** — version control and portfolio hosting

---

## Project Structure

```
customer-shopping-behavior-analysis/
│
├── decoding_shoppers_analysis.ipynb            # Python: data cleaning, feature engineering, EDA
├── customer_data.csv                           # Cleaned dataset, output of the notebook
├── decoding_shoppers_queries.sql               # 15 SQL business-question queries (PostgreSQL)
├── decoding_shoppers_dashboard_v2.pbix         # Power BI dashboard (Overview + Deep Dive pages)
├── assets/
│   └── dashboard_overview-page.png                  # Dashboard screenshot(s)
└── README.md                                   # Project documentation (this file)
```

---

## Data Cleaning & Preparation

Performed in Python (`decoding_shoppers_analysis.ipynb`):

1. **Data loading** — imported the raw dataset with Pandas.
2. **Initial exploration** — used `.info()` and `.describe()` to understand structure, types, and distribution.
3. **Missing data handling** — imputed 37 missing `review_rating` values using the median rating per product category.
4. **Column standardization** — renamed all columns to snake_case for consistency.
5. **Feature engineering:**
   - `age_group` — created by binning customer ages
   - `purchase_frequency_days` — derived from purchase frequency data
6. **Redundancy check** — verified `discount_applied` and `promo_code_used` were duplicating the same signal; dropped `promo_code_used`.
7. **Outlier detection** — IQR-based check and boxplot visualization on `purchase_amount`.
8. **Correlation analysis** — heatmap across `age`, `purchase_amount`, `review_rating`, and `previous_purchases` to check for relationships between numeric features.
9. **Export** — cleaned dataset exported to `cleaned_customer_data.csv` and loaded into PostgreSQL via pgAdmin for SQL analysis.

---

## EDA — Key Insights

- Purchase amounts range narrowly ($20–$100, mean ≈ $59.76) with no significant outliers detected via IQR.
- No strong linear correlation between `review_rating` and `purchase_amount` — spend isn't simply driven by satisfaction.
- Only 27% of customers are active subscribers, despite average order values comparable to non-subscribers — signaling an upsell opportunity rather than a value gap.

---

## SQL Analysis (PostgreSQL)

15 business questions answered via SQL — full queries in `decoding_shoppers_queries.sql`. Highlights:

1. Revenue by gender
2. High-spending customers who still used discounts
3. Top 5 products by average review rating
4. Purchase amount: Standard vs. Express shipping
5. Subscriber vs. non-subscriber spend comparison
6. Products with the highest discount dependency
7. Customer segmentation — New / Returning / Loyal
8. Top 3 products per category
9. Repeat buyers vs. subscription likelihood
10. Revenue by age group
11. Top 10 locations by revenue
12. Revenue and average spend by season
13. Revenue and customer count by payment method
14. Spend by purchase frequency (weekly/monthly/annual)
15. Review rating vs. repeat purchase behavior (loyalty correlation)

---

## Dashboard (Power BI)

A custom-themed, 2-page interactive dashboard:

**Page 1 — Overview:** KPI cards (Total Revenue, Customers, Average Order Value, Average Rating, Subscription Rate, Repeat Buyer Rate), a category revenue treemap, a customer-segment donut, a rating-distribution chart, a filled map of revenue by state, season and payment-method breakdowns, and a category-level hover tooltip showing top products.

**Page 2 — Deep Dive:** A drill-through page — clicking any state on the map jumps here, automatically filtered to that state, showing its top 5 products, payment split, age group, and seasonal breakdown, with a dynamic breadcrumb title and a back button.

https://github.com/Vipparti-Vinay/customer-behavior-retention-analysis-python-sql-powebi/blob/main/dashboard_overview_page.png



---

## Results and Conclusion

**Key findings:**
- Male customers generated roughly 2x the revenue of female customers.
- Only 27% of the customer base is subscribed, yet subscriber spend is comparable to non-subscribers — a clear conversion opportunity.
- 3,116 customers fall into the "Loyal" segment vs. just 701 "Returning" and 83 "New" — retention is strong, but the top of the acquisition funnel is thin.
- Categories like Hats and Sneakers show discount rates near 50%, raising margin concerns.
- Express shipping customers spend marginally more on average than Standard shipping customers.

**Business recommendations:**
- Promote subscription benefits to convert high-spending non-subscribers.
- Build loyalty incentives specifically targeting "Returning" customers to move them into "Loyal."
- Review discount policy on high-discount-dependency products to protect margins.
- Prioritize marketing spend in top-revenue locations and seasons identified in the SQL analysis.
- Invest in top-of-funnel acquisition channels, given the thin "New" customer segment.

---

## Author and Contact

**Vipparti Vinay**
📧 Email: vinayvipparti.in@gmail.com
💼 LinkedIn: [add your LinkedIn profile link]
🌐 Portfolio: [add your portfolio link]

*Originally guided by [Amlan Mohanty's](https://www.youtube.com/@amlanmohanty1) Customer Behavior Data Analyst Portfolio Project tutorial, extended with additional analysis and a custom dashboard redesign.*
