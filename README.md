# 📊 SQL Data Analytics Project

Exploratory and advanced analytical SQL project built on top of the **[SQL Data Warehouse Project](https://github.com/Yashkashyap619/SQL-Data-Warehouse-Project)**. Where the warehouse project focuses on *engineering* — building and modeling the data — this project focuses on *analysis*: turning the Gold layer's star schema into business insights using pure SQL.

This repository contains **13 structured SQL scripts (850+ lines)** that walk through a complete analytics workflow — from exploring the database to building reusable, view-based customer and product reports — following a standard EDA → Advanced Analytics → Reporting framework.

---

## 🏗️ How This Fits the Bigger Picture

```
SQL-Data-Warehouse-Project          sql-data-analytics-project
   (Data Engineering)          →         (Data Analysis)
   Bronze → Silver → Gold              Gold Layer → Insights
   ETL, cleansing, modeling            EDA, KPIs, segmentation,
   Star schema (fact + 2 dims)         trend & performance reports
```

This project consumes the `gold.fact_sales`, `gold.dim_customers`, and `gold.dim_products` objects produced by the warehouse project and answers real business questions against them — no raw data wrangling required, since that work is already done upstream.

---

## 🎯 Objective

Develop SQL-based analytics to explore the data, calculate key business metrics, and deliver actionable insights into:
- **Customer Behavior** — who buys, how often, and how much
- **Product Performance** — what sells, what doesn't, and why
- **Sales Trends** — how the business is growing (or not) over time

---

## 🧭 Analytical Framework

The project follows a two-stage analytics framework — first understand the data (EDA), then answer business questions with it (Advanced Analytics) — before packaging the results into reusable reports.

### 🔍 Exploratory Data Analysis (EDA)

| # | Script | What It Covers |
|---|--------|-----------------|
| 1 | `01_database_exploration.sql` | Inspecting database objects, tables, and columns (metadata exploration) |
| 2 | `02_dimensions_exploration.sql` | `DISTINCT` values across key dimensions (countries, categories, products) |
| 3 | `03_date_range_exploration.sql` | `MIN`/`MAX`/`DATEDIFF` to find the boundaries and span of the data |
| 4 | `04_measures_exploration.sql` | Key business metrics — total sales, orders, quantity, average price |
| 5 | `05_magnitude_analysis.sql` | Measures broken down by dimensions (e.g., total sales by country) |
| 6 | `06_ranking_analysis.sql` | `TOP N` / `RANK()` / `DENSE_RANK()` to find best & worst performers |

### 📈 Advanced Analytics

| # | Script | What It Covers |
|---|--------|-----------------|
| 7 | `07_change_over_time_analysis.sql` | Trend analysis of sales/orders by year and month |
| 8 | `08_cumulative_analysis.sql` | Running totals and moving averages using `SUM() OVER()` / `AVG() OVER()` |
| 9 | `09_performance_analysis.sql` | Year-over-Year growth using `LAG()`, plus performance vs. average using window `AVG()` |
| 10 | `10_data_segmentation.sql` | `CASE`-based segmentation — product cost bands, customer VIP/Regular/New tiers |
| 11 | `11_part_to_whole_analysis.sql` | Proportional analysis — each category's % contribution to total sales |

### 📋 Final Reports (Reusable SQL Views)

| # | Script | Output |
|---|--------|--------|
| 12 | `12_report_customers.sql` | `gold.report_customers` — consolidated customer view with segmentation (VIP/Regular/New), age groups, recency, total orders/sales/quantity, lifespan, average order value, and average monthly spend |
| 13 | `13_report_products.sql` | `gold.report_products` — consolidated product view with performance segmentation (High/Mid/Low), total orders/sales/quantity, unique customers, lifespan, average order revenue, and average monthly revenue |

These two views are the deliverable — analyst-ready, single-query customer and product summaries that could plug directly into a BI tool (Power BI/Tableau) or be queried on demand.

---

## 🛠️ SQL Techniques & Functions Used

- **Window Functions:** `RANK()`, `DENSE_RANK()`, `ROW_NUMBER()`, `LAG()`, `SUM() OVER()`, `AVG() OVER()`, `PARTITION BY`
- **CTEs (Common Table Expressions):** multi-step, layered logic in every report and analysis script
- **Conditional Logic:** `CASE WHEN` for segmentation and trend classification (Above/Below Avg, Increase/Decrease)
- **Date Functions:** `DATEDIFF`, `DATETRUNC`, `YEAR()`, `GETDATE()`
- **Aggregations:** `SUM`, `AVG`, `COUNT(DISTINCT …)` at both row and grouped levels
- **Views:** persisted, reusable analytical objects (`gold.report_customers`, `gold.report_products`)

---

## 📂 Repository Structure

```
sql-data-analytics-project/
│
├── datasets/               # Gold-layer CSVs consumed by the analysis (customers, products, sales)
├── docs/                   # Project roadmap and planning notes
├── scripts/
│   ├── 00_init_database.sql
│   ├── 01-06_*.sql         # Exploratory Data Analysis
│   ├── 07-11_*.sql         # Advanced Analytics
│   └── 12-13_*.sql         # Final customer & product reports (views)
├── README.md
└── LICENSE
```

---

## 🚀 How to Use

1. Run `00_init_database.sql` to create the `DataWarehouseAnalytics` database.
2. Load the Gold-layer CSVs in `datasets/csv-files/` (or run the upstream [warehouse project](https://github.com/Yashkashyap619/SQL-Data-Warehouse-Project) to generate them fresh).
3. Run scripts `01` through `11` in order to reproduce the exploratory and advanced analysis.
4. Run `12_report_customers.sql` and `13_report_products.sql` to create the two reporting views.
5. Query `gold.report_customers` / `gold.report_products` directly, or connect a BI tool to them.

---

## 🧰 Tools & Skills

**SQL Server (T-SQL)** · Window Functions · CTEs · Data Segmentation · KPI Design · Exploratory Data Analysis · Trend & Performance Analysis · View-Based Reporting

---

## 🛡️ License

This project is licensed under the [MIT License](LICENSE). Free to use, modify, and share with proper attribution.

## 🔗 Related

- [SQL Data Warehouse Project](https://github.com/Yashkashyap619/SQL-Data-Warehouse-Project) — the upstream ETL & data modeling project this analysis is built on
