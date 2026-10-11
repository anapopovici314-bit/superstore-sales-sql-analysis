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
---

2. **Data Warehousing & Querying (BigQuery):**
   * Imported the cleaned dataset into BigQuery.
   * Wrote and executed complex SQL queries to extract valuable business metrics.

---

## 📊 SQL Analysis & Key Insights
The following analytical queries were implemented in BigQuery (`queries.sql`):
1. **Top Product Categories:** Identified the best-performing product categories by total sales.
```sql
SELECT 
    Category,
    ROUND(SUM(Sales), 2) AS Total_Sales
FROM 
    `tidy-elf-498016-j2.Sales_dataset.sales`
GROUP BY 
    Category
ORDER BY 
    Total_Sales DESC;
```

2. **Regional Sales & Orders Performance:** Evaluated total revenue and order volume across different geographical regions.
```sql
SELECT 
    Region,
    COUNT(DISTINCT Order_ID) AS Total_Orders,
    ROUND(SUM(Sales), 2) AS Total_Sales
FROM 
    `tidy-elf-498016-j2.Sales_dataset.sales`
GROUP BY 
    Region
ORDER BY 
    Total_Sales DESC;
```

3. **Customer Loyalty Analysis:** Ranked customers based on their purchase frequency and total spending behavior.
```sql
SELECT 
    Customer_ID,
    Customer_Name,
    Segment,
    COUNT(DISTINCT Order_ID) AS Total_Orders
FROM 
    `tidy-elf-498016-j2.Sales_dataset.sales`
GROUP BY 
    Customer_ID, Customer_Name, Segment
ORDER BY 
    Total_Orders DESC
LIMIT 5;
```

4. **Advanced Customer Segmentation (Window Functions & CTEs):** Utilized `ROW_NUMBER()` and `PARTITION BY` clauses within a Common Table Expression (CTE) to isolate the **Top 3 customers per region** based on sales volume.
```sql
WITH RankedCustomers AS (
    SELECT 
        Region,
        Customer_ID,
        Customer_Name,
        ROUND(SUM(Sales), 2) AS Total_Sales,
        ROW_NUMBER() OVER (PARTITION BY Region ORDER BY SUM(Sales) DESC) AS rank_num
    FROM 
        `numele_proiectului.nume_dataset.superstore_final_dataset`
    GROUP BY 
        Region, Customer_ID, Customer_Name
)
SELECT 
    Region,
    Customer_Name,
    Total_Sales,
    rank_num
FROM 
    RankedCustomers
WHERE 
    rank_num <= 3
ORDER BY 
    Region, rank_num;
```

---

## 📂 Repository Structure
```text
├── data/                  # Cleaned dataset sample or references
├── sql/                   # SQL scripts containing all analytical queries
└── README.md              # Project documentation
