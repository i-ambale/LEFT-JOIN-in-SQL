# Recreating the Access_to_Basic_Services Dataset
Understanding Database Joins with ERDs and LEFT JOIN Techniques

---
## 📌 Overview
This project demonstrates how Entity-Relationship Diagrams (ERDs) guide effective database joins, with a focus on the `LEFT JOIN`technique. Using the `united_nations` database, we analyze relationships between:

- `Geographic_Location` (central table)

- `Basic_Services`

- `Economic_Indicators`

Incorrect joins can lead to inaccurate results, so choosing the right strategy is critical.

---
## 🎯 Learning Objectives
By the end of this project, you will:

1. Interpret ERDs to determine table relationships and join strategies.

2. Apply LEFT JOINs to combine tables while preserving all records from the "left" table.

3. Evaluate join strategies to avoid data inconsistencies (e.g., NULL values for non-matches).

---
## 📊 Database Schema (ERD)
The `united_nations` database consists of:

- Geographic_Location: Country-level geographic data (e.g., `Country_name`, `Region`, `Land_area`).

- Basic_Services: Metrics on access to services (e.g., sanitation, water).

- Economic_Indicators: Economic metrics (e.g., GDP, unemployment).

Tables are linked via `Country_name` as the primary key.

---
## 🔍 Key SQL Techniques
LEFT JOIN Example
```
SELECT
    gl.Country_name,
    gl.Region,
    bs.Access_to_sanitation,
    ei.GDP_per_capita
FROM
    Geographic_Location gl
LEFT JOIN
    Basic_Services bs ON gl.Country_name = bs.Country_name
LEFT JOIN
    Economic_Indicators ei ON gl.Country_name = ei.Country_name
LIMIT 100;
```
## Why LEFT JOIN?

- Ensures all countries (even those missing economic/service data) are included.

- Non-matches return `NULL` for right-table columns.

---
## ⚠️ Common Pitfalls
1. Incorrect Join Type: Using `INNER JOIN` instead of `LEFT JOIN` may exclude countries with missing data.

2. Ambiguous Column Names: Always prefix columns with table aliases (e.g., `gl.Country_name`).

3. Performance: Use `LIMIT` for large datasets.

---
## 🛠️ Setup Instructions
1. Prerequisites:

  - MySQL Workbench installed locally.
  
  - `united_nations` database set up (same machine as this notebook).

2. Note: This notebook will not run on Google Colab (requires local MySQL connection).

---
## 📚 Resources
- [MySQL JOIN Documentation](https://dev.mysql.com/doc/refman/8.0/en/join.html)

- [ERD Design Best Practicesh](https://www.lucidchart.com/pages/er-diagrams)
