# 📊 Data Warehouse and Analytics Project

Welcome to the **Data Warehouse and Analytics Project** repository! 🚀  
This project demonstrates an **end-to-end modern data warehousing and analytics solution**, built using **SQL Server** and **Medallion Architecture (Bronze, Silver, Gold)**.

It is designed as a **portfolio project** to showcase best practices in **Data Engineering, Data Modeling, ETL pipelines, and Analytics**.

---

## 🏗️ Data Architecture

This project follows the **Medallion Architecture** pattern:

![Data Architecture](https://raw.githubusercontent.com/MOHDAKRAM43/sql-data-warehouse-project/main/docs/Data_Architecture.png)


- **Bronze Layer** – Raw data ingestion from source systems  
- **Silver Layer** – Data cleansing, standardization, and transformation  
- **Gold Layer** – Business-ready data modeled for analytics and reporting  


---

## 📖 Project Overview

This project covers the complete lifecycle of a data warehouse:

- **Data Architecture Design** using Medallion Architecture
- **ETL Pipelines** for CRM and ERP source systems
- **Data Quality Handling** (nulls, duplicates, invalid values)
- **Dimensional Data Modeling** (Star Schema)
- **SQL-Based Analytics & Reporting**

---

## 🎯 Skills Demonstrated

This repository showcases hands-on experience in:

- SQL Development  
- Data Engineering  
- Data Warehousing  
- ETL Pipeline Development  
- Data Modeling (Star Schema)  
- Data Analytics & Reporting  

---

## 🛠️ Tools & Technologies

All tools used in this project are **free and open-source**:

- **SQL Server Express** – Database engine  
- **SQL Server Management Studio (SSMS)** – Database management  
- **CSV Files** – Source data (ERP & CRM)  
- **Git & GitHub** – Version control and collaboration  
- **Draw.io** – Architecture, data models, and flow diagrams  
- **Notion** – Project planning and documentation  

---

## 🚀 Project Requirements

### 🏗️ Data Engineering – Building the Data Warehouse

**Objective:**  
Develop a modern data warehouse using SQL Server to consolidate sales data and enable analytical reporting.

**Specifications:**
- **Data Sources:** ERP and CRM systems (CSV files)
- **Data Quality:** Clean and resolve inconsistencies before analysis
- **Integration:** Merge multiple sources into a unified analytical model
- **Scope:** Latest data only (no historization)
- **Documentation:** Clear data models and metadata

---

### 📊 BI & Analytics – Reporting & Insights

**Objective:**  
Develop SQL-based analytics to generate insights into:

- Customer Behavior  
- Product Performance  
- Sales Trends  

These insights help stakeholders make **data-driven decisions**.

For detailed requirements, see:  
📄 `docs/requirements.md`

---

## 🧱 Data Layers Overview

### 🥉 Bronze Layer
- Stores **raw source data** as-is
- One-to-one mapping with source systems
- No transformations applied

### 🥈 Silver Layer
- Data cleansing and standardization
- Deduplication and validation
- Business-friendly formatting

### 🥇 Gold Layer
- Analytics-ready data
- Star schema with **fact** and **dimension** tables
- Optimized for reporting and dashboards

---

## 📚 Gold Layer Data Model

### `gold.dim_customers`
Stores enriched customer information including demographics and geography.

### `gold.dim_products`
Contains product details, categories, and attributes.

### `gold.fact_sales`
Holds transactional sales data for analytical queries.

Detailed field descriptions are available in:  
📄 `docs/data_catalog.md`

---

## 📐 Naming Conventions

Consistent naming standards are applied across all layers.

### General Rules
- `snake_case`
- English language
- Avoid SQL reserved keywords

### Layer Rules
- **Bronze:** `<source>_<entity>`  
- **Silver:** `<source>_<entity>`  
- **Gold:**  
  - `dim_<entity>` → Dimension tables  
  - `fact_<entity>` → Fact tables  

📄 Full details: `docs/naming-conventions.md`

---

## 📂 Repository Structure

```text
data-warehouse-project/
│
├── datasets/                   # Raw ERP & CRM datasets (CSV)
│
├── docs/                       # Documentation & diagrams
│   ├── etl.drawio
│   ├── data_architecture.drawio
│   ├── Data_Architecture.png
│   ├── data_catalog.md
│   ├── data_flow.drawio
│   ├── data_models.drawio
│   ├── naming-conventions.md
│
├── scripts/
│   ├── bronze/                 # Raw data load scripts
│   ├── silver/                 # Cleansing & transformation scripts
│   ├── gold/                   # Dim & fact table scripts
│
├── tests/                      # Data quality & validation scripts
│
├── README.md
├── LICENSE
├── .gitignore
└── requirements.txt
```
----

## ☕ Stay Connected

Let’s connect and grow together 🚀

🔗 LinkedIn: [(https://www.linkedin.com/in/mohd-akram-6a210a259/)]

💻 GitHub: [https://github.com/MOHDAKRAM43]

📧 Gmail: [imakram7860@gmail.com]

Your support through starring, and sharing means a lot ❤️
Thank you.



