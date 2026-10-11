# superstore-sales-sql-analysis

## 📌 Project Overview
This project demonstrates an end-to-end data analytics workflow using an **E-Commerce / Superstore Sales dataset**. The goal of this project is to clean, process, and analyze sales performance, regional trends, and customer behavior using **Microsoft Excel** and **Google BigQuery (SQL)**.

---

## 🛠️ Tools & Technologies Used
* **Microsoft Excel:** Data cleaning, formatting validation, missing value checks, and custom data attribute additions.
* **Google BigQuery (SQL):** Cloud-based data warehousing, aggregation, data filtering, and advanced window functions.
* **GitHub:** Version control and portfolio presentation.

---

## 🔍 Key Steps & Workflow
1. **Data Cleaning & Preparation (Excel):**
   * Inspected dataset for structural consistency and handled date formatting.
   * Standardized text formats and ensured numeric fields (Sales, Profit) were properly recognized.
   * Handled missing attributes and enriched data fields for advanced calculations.

2. **Data Warehousing & Querying (BigQuery):**
   * Imported the cleaned dataset into BigQuery.
   * Wrote and executed complex SQL queries to extract valuable business metrics.

---

## 📊 SQL Analysis & Key Insights
The following analytical queries were implemented in BigQuery (`queries.sql`):
1. **Top Product Categories:** Identified the best-performing product categories by total sales.
2. **Regional Sales & Orders Performance:** Evaluated total revenue and order volume across different geographical regions.
3. **Customer Loyalty Analysis:** Ranked customers based on their purchase frequency and total spending behavior.
4. **Advanced Customer Segmentation (Window Functions & CTEs):** Utilized `ROW_NUMBER()` and `PARTITION BY` clauses within a Common Table Expression (CTE) to isolate the **Top 3 customers per region** based on sales volume.

---

## 📂 Repository Structure
```text
├── data/                  # Cleaned dataset sample or references
├── sql/                   # SQL scripts containing all analytical queries
└── README.md              # Project documentation
