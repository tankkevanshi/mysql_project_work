# 🗄️ MySQL Data Digger

> A practical SQL project focused on relational database design, data manipulation, analysis, and business-oriented querying using MySQL.

---

## 📌 Project Overview

**MySQL Data Digger** is a hands-on MySQL project designed to demonstrate how relational databases can be created, structured, managed, and analyzed using SQL.

The project uses an e-commerce-style database environment to work with customers, orders, products, and order details.

It covers SQL fundamentals as well as practical data-analysis techniques such as aggregation, sorting, filtering, joins, and subqueries.

---

## 🎯 Objectives

The main objectives of this project are to:

- Build and understand a relational database structure
- Create and manage database tables
- Work with primary and foreign keys
- Perform CRUD operations
- Retrieve meaningful information using SQL
- Analyze numerical and transactional data
- Apply aggregate functions for business analysis
- Use JOINs to combine related data
- Apply subqueries for advanced filtering
- Practice real-world SQL problem solving

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| **MySQL** | Relational database management |
| **SQL** | Data manipulation and analysis |
| **MySQL Command Line** | Query execution and testing |

---

## 🗃️ Database Structure

The project works with an e-commerce-oriented relational database.

### Core Tables

#### 👤 Customers

Stores customer information such as:

- Customer ID
- Name
- Email
- Address

#### 🛒 Orders

Stores customer order information:

- Order ID
- Customer ID
- Order Date
- Total Amount

#### 📦 Products

Stores product information:

- Product ID
- Product Name
- Price
- Stock

#### 🧾 Order Details

Stores detailed information about products included in orders:

- Order Detail ID
- Order ID
- Product ID
- Quantity
- SubTotal

---

## 🔗 Database Relationships

The project demonstrates relationships between entities using primary and foreign keys.

```text
Customers
    │
    │ CustomerID
    ▼
Orders
    │
    │ OrderID
    ▼
Order Details
    │
    │ ProductID
    ▼
Products
