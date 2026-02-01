# Gold Layer – Data Catalog

## 📌 Overview

The **Gold Layer** represents the business-ready, curated data model designed for **analytics, reporting, and BI consumption**.
It follows a **star schema** approach, consisting of **dimension tables** and **fact tables** that provide consistent, reliable metrics across the organization.

This layer is sourced from the **Silver Layer**, where data is already cleansed, standardized, and validated.

---

## 🏗️ Data Model

* **Dimensions**: Descriptive business entities (Customers, Products)
* **Facts**: Transactional measures (Sales)
* **Grain**: One row per business event (e.g., one product per order line)

---

## 📊 Dimension Tables

### 1️⃣ `gold.dim_customers`

**Purpose**
Stores enriched customer information including demographic and geographic attributes. This table acts as the **customer master** for analytics.

**Grain**
One row per customer.

| Column Name     | Data Type    | Description                                        |
| --------------- | ------------ | -------------------------------------------------- |
| customer_key    | INT          | Surrogate key uniquely identifying each customer   |
| customer_id     | INT          | Unique numeric identifier assigned to the customer |
| customer_number | NVARCHAR(50) | Business/customer reference number                 |
| first_name      | NVARCHAR(50) | Customer first name                                |
| last_name       | NVARCHAR(50) | Customer last name                                 |
| country         | NVARCHAR(50) | Customer country of residence                      |
| marital_status  | NVARCHAR(50) | Marital status (Married, Single, n/a)              |
| gender          | NVARCHAR(50) | Gender derived from CRM and ERP sources            |
| birthdate       | DATE         | Customer date of birth (YYYY-MM-DD)                |
| create_date     | DATE         | Customer record creation date                      |

---

### 2️⃣ `gold.dim_products`

**Purpose**
Contains product master data including classification, pricing, and lifecycle information.

**Grain**
One row per product.

| Column Name          | Data Type    | Description                         |
| -------------------- | ------------ | ----------------------------------- |
| product_key          | INT          | Surrogate key for the product       |
| product_id           | INT          | Internal product identifier         |
| product_number       | NVARCHAR(50) | Business product code               |
| product_name         | NVARCHAR(50) | Descriptive product name            |
| category_id          | NVARCHAR(50) | Category identifier                 |
| category             | NVARCHAR(50) | Product category (e.g., Bikes)      |
| subcategory          | NVARCHAR(50) | Product subcategory                 |
| maintenance_required | NVARCHAR(50) | Indicates maintenance requirement   |
| cost                 | INT          | Product base cost                   |
| product_line         | NVARCHAR(50) | Product line (Road, Mountain, etc.) |
| start_date           | DATE         | Product availability start date     |

---

## 📈 Fact Tables

### 3️⃣ `gold.fact_sales`

**Purpose**
Stores transactional sales data used to analyze revenue, quantity sold, and customer purchasing behavior.

**Grain**
One row per **product per order**.

| Column Name   | Data Type    | Description                    |
| ------------- | ------------ | ------------------------------ |
| order_number  | NVARCHAR(50) | Unique sales order identifier  |
| product_key   | INT          | Foreign key to `dim_products`  |
| customer_key  | INT          | Foreign key to `dim_customers` |
| order_date    | DATE         | Date the order was placed      |
| shipping_date | DATE         | Date the order was shipped     |
| due_date      | DATE         | Payment due date               |
| sales_amount  | INT          | Total sales amount             |
| quantity      | INT          | Quantity sold                  |
| price         | INT          | Price per unit                 |

---

## 🔗 Relationships

* `fact_sales.customer_key` → `dim_customers.customer_key`
* `fact_sales.product_key` → `dim_products.product_key`

This ensures **referential integrity** and enables accurate dimensional analysis.

---

## 🔄 Data Lineage

```
Source Systems
   ↓
Bronze Layer  (Raw ingestion)
   ↓
Silver Layer  (Cleansed & standardized)
   ↓
Gold Layer    (Business-ready analytics model)
```

---

## ✅ Usage Examples

* Customer demographic analysis
* Sales trend and revenue reporting
* Product performance dashboards
* Country-wise and category-wise KPIs

---

## 📝 Notes

* All surrogate keys are generated in the Gold Layer.
* Null or unknown values are standardized as `'n/a'`.
* This layer is optimized for **Power BI, Tableau, and SQL-based analytics**.

---

📌 **Owner**: MOhd Akram
📌 **Layer**: Gold
📌 **Model Type**: Star Schema
