# 🚀 PR-2 — Data Transformer

> **Advanced MySQL Data Transformation & Analytical Querying Project**

## 📌 Project Overview

**Data Transformer** is an advanced SQL project developed using **MySQL** to demonstrate practical data transformation, relational data analysis, and analytical querying techniques.

The project transforms structured customer, order, and employee data into meaningful business insights using advanced SQL concepts such as **JOINs, subqueries, aggregate functions, conditional expressions, date/string transformations, and window functions**.

---

## 🎯 Project Objectives

The primary objective of this project is to build strong practical expertise in:

* Relational database querying
* Data transformation and preparation
* Multi-table data integration
* Business-oriented data analysis
* Advanced SQL functions
* Analytical window functions
* Conditional data classification
* Ranking and cumulative calculations
* Extracting insights from transactional data

---

## 🏗️ Database Architecture

```text
                    ┌──────────────────┐
                    │    Customers     │
                    ├──────────────────┤
                    │ CustomerID (PK)  │
                    │ FirstName        │
                    │ LastName         │
                    │ Email            │
                    └────────┬─────────┘
                             │
                             │ CustomerID
                             │
                    ┌────────▼─────────┐
                    │      Orders      │
                    ├──────────────────┤
                    │ OrderID (PK)     │
                    │ CustomerID (FK)  │
                    │ OrderDate        │
                    │ TotalAmount      │
                    └──────────────────┘


                    ┌──────────────────┐
                    │    Employees     │
                    ├──────────────────┤
                    │ EmployeeID (PK)  │
                    │ EmployeeName     │
                    │ Department       │
                    │ Salary           │
                    └──────────────────┘
```

---

## 🗄️ Database Components

### Customers

Contains customer-level information used for customer analysis and order relationships.

### Orders

Contains transactional information used for revenue, ranking, cumulative totals, and customer-order analysis.

### Employees

Contains employee information used for salary analysis, department-level calculations, and classification.

---

# 🔥 Advanced SQL Techniques

## 1. Multi-Table JOIN Operations

The project demonstrates relational data integration using different JOIN strategies.

```sql
SELECT
    C.CustomerID,
    C.FirstName,
    C.LastName,
    O.OrderID,
    O.TotalAmount
FROM Customers C
JOIN Orders O
    ON C.CustomerID = O.CustomerID;
```

### Concepts Demonstrated

* `INNER JOIN`
* `LEFT JOIN`
* `RIGHT JOIN`
* `UNION` for FULL OUTER JOIN-style analysis

---

## 2. Subquery-Based Analysis

Subqueries are used to compare individual records against dynamically calculated values.

### Example

```sql
SELECT
    C.CustomerID,
    C.FirstName,
    C.LastName
FROM Customers C
JOIN Orders O
    ON C.CustomerID = O.CustomerID
WHERE O.TotalAmount >
      (
          SELECT AVG(TotalAmount)
          FROM Orders
      );
```

### Analytical Purpose

Identifies customers whose order value is **above the overall average order amount**.

---

# 📊 3. Aggregate Functions

The project applies aggregate functions for business-level calculations.

```sql
SELECT
    CustomerID,
    SUM(TotalAmount) AS TotalSpent,
    AVG(TotalAmount) AS AverageOrderValue,
    MAX(TotalAmount) AS HighestOrder
FROM Orders
GROUP BY CustomerID;
```

### Functions Used

* `SUM()`
* `AVG()`
* `MAX()`
* `MIN()`
* `COUNT()`

---

# 🪟 4. Window Functions

Advanced analytical calculations are performed without collapsing individual rows.

### Running Total

```sql
SELECT
    OrderID,
    OrderDate,
    TotalAmount,
    SUM(TotalAmount) OVER (
        ORDER BY OrderDate
    ) AS RunningTotal
FROM Orders;
```

### Ranking

```sql
SELECT
    OrderID,
    TotalAmount,
    RANK() OVER (
        ORDER BY TotalAmount DESC
    ) AS OrderRank
FROM Orders;
```

### Window Concepts

* `SUM() OVER()`
* `RANK() OVER()`
* `PARTITION BY`
* `ORDER BY`
* Running calculations
* Analytical ranking

---

# 🧠 5. Conditional Data Transformation

Business rules are implemented using `CASE`.

```sql
SELECT
    EmployeeName,
    Salary,
    CASE
        WHEN Salary >= 60000 THEN 'High'
        WHEN Salary >= 40000 THEN 'Medium'
        ELSE 'Low'
    END AS SalaryCategory
FROM Employees;
```

This converts numerical salary information into meaningful business categories.

---

# 📅 6. Date Transformation

The project demonstrates extraction and transformation of date information.

### Functions

```sql
YEAR()
MONTH()
DATEDIFF()
DATE_FORMAT()
```

### Example

```sql
SELECT
    OrderID,
    OrderDate,
    YEAR(OrderDate) AS OrderYear,
    MONTH(OrderDate) AS OrderMonth
FROM Orders;
```

---

# 🔤 7. String Transformation

Customer and employee information can be cleaned and formatted using SQL string functions.

### Functions Used

```text
CONCAT()
UPPER()
LOWER()
TRIM()
REPLACE()
```

### Example

```sql
SELECT
    CONCAT(
        FirstName,
        ' ',
        LastName
    ) AS FullName
FROM Customers;
```

---

# 📈 Analytical Use Cases

The project demonstrates how SQL can answer practical business questions such as:

### Customer Analysis

* Which customers placed orders?
* Which customers have above-average order values?
* What is the total amount spent by each customer?
* How can customer names be transformed and standardized?

### Order Analysis

* What is the highest-value order?
* How can orders be ranked?
* What is the cumulative order amount?
* How can order dates be transformed for reporting?

### Employee Analysis

* Which employees earn above the average salary?
* How can employees be classified by salary level?
* How can salary information be transformed into business categories?

---

# 🔄 Data Transformation Pipeline

```text
        Raw Data
           │
           ▼
   ┌─────────────────┐
   │ Data Retrieval  │
   └────────┬────────┘
            │
            ▼
   ┌─────────────────┐
   │ JOIN Operations │
   └────────┬────────┘
            │
            ▼
   ┌─────────────────┐
   │ Aggregation     │
   │ & Subqueries    │
   └────────┬────────┘
            │
            ▼
   ┌─────────────────┐
   │ Transformation  │
   │ Date / String   │
   └────────┬────────┘
            │
            ▼
   ┌─────────────────┐
   │ Window Analysis │
   │ Ranking / Total  │
   └────────┬────────┘
            │
            ▼
      Business Insights
```

---

# 🛠️ Technology Stack

| Technology                | Purpose                           |
| ------------------------- | --------------------------------- |
| **MySQL**                 | Database Management               |
| **SQL**                   | Data Querying                     |
| **MySQL Workbench / CLI** | Query Execution                   |
| **GitHub**                | Version Control & Project Hosting |

---

# 📂 Project Structure

```text
mysql_project_work/
│
├── PR_2_Data Transformer.sql
│
└── README.md
```

---

# ▶️ How to Execute

### Step 1 — Open MySQL

Use MySQL Workbench or MySQL CLI.

### Step 2 — Create Database

```sql
CREATE DATABASE data_transfer;
```

### Step 3 — Select Database

```sql
USE data_transfer;
```

### Step 4 — Execute SQL Script

Run:

```text
PR_2_Data Transformer.sql
```

### Step 5 — Verify Tables

```sql
SHOW TABLES;
```

Expected structure:

```text
Customers
Employees
Orders
```

---

# 📊 Expected Analytical Outputs

The project generates transformed and analytical datasets containing:

* Customer-order relationships
* Above-average order analysis
* Employee salary comparisons
* Salary classifications
* Formatted customer names
* Extracted order dates
* Running totals
* Transaction rankings
* Aggregated customer spending

---

# 🧩 SQL Skills Demonstrated

```text
✓ Database Creation
✓ Table Creation
✓ Data Insertion
✓ SELECT Queries
✓ Filtering
✓ Sorting
✓ GROUP BY
✓ Aggregate Functions
✓ INNER JOIN
✓ LEFT JOIN
✓ RIGHT JOIN
✓ UNION
✓ Subqueries
✓ CASE Expressions
✓ Date Functions
✓ String Functions
✓ Window Functions
✓ RANK()
✓ SUM() OVER()
✓ Running Totals
✓ Data Transformation
✓ Analytical Reporting
```

---

# 💡 Key Learning Outcomes

Through this project, the following advanced SQL capabilities are demonstrated:

1. **Transforming raw relational data into analytical datasets**
2. **Combining multiple tables using relational joins**
3. **Using subqueries for dynamic comparisons**
4. **Performing aggregation for business analysis**
5. **Applying window functions for row-level analytics**
6. **Creating business classifications with conditional logic**
7. **Manipulating date and text-based information**
8. **Building reusable analytical SQL queries**

---

# 🚀 Future Enhancements

The project can be extended with:

* Common Table Expressions `(CTEs)`
* Stored Procedures
* Views
* Triggers
* Index Optimization
* Query Performance Analysis
* Advanced Window Functions
* Customer Segmentation
* Revenue Trend Analysis
* Department-Level Analytics
* SQL-based Reporting Dashboards

---

# 👩‍💻 Author

**Kevanshi Tank**

### Project

**PR-2 — Data Transformer**

### Focus

**Advanced MySQL | Data Transformation | SQL Analytics**

---

⭐ **This project demonstrates the practical application of MySQL for relational data transformation, analytical querying, and business-oriented data analysis.**
