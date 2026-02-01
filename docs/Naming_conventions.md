# Naming Conventions

This document defines the **standard naming conventions** used across the data warehouse for schemas, tables, columns, and stored procedures. Following these conventions ensures **consistency, readability, maintainability, and scalability** across all data layers.

---

## 📑 Table of Contents

1. General Principles
2. Table Naming Conventions

   * Bronze Layer Rules
   * Silver Layer Rules
   * Gold Layer Rules
3. Glossary of Category Patterns
4. Column Naming Conventions

   * Surrogate Keys
   * Technical Columns
5. Stored Procedure Naming Conventions

---

## 1️⃣ General Principles

* **Naming Style**: Use `snake_case` (lowercase letters with underscores `_`).
* **Language**: All object names must be in **English**.
* **Clarity**: Names should clearly describe the business meaning or technical purpose.
* **Avoid Reserved Words**: SQL reserved keywords must not be used as object names.
* **Consistency**: The same naming pattern must be applied across all layers.

---

## 2️⃣ Table Naming Conventions

### 🔹 Bronze Layer Rules

* Table names must start with the **source system name**.
* Table names must match the **original source table names** exactly.
* No business renaming or transformation is allowed at this layer.

**Pattern**

```
<sourcesystem>_<entity>
```

* `<sourcesystem>`: Name of the source system (e.g., `crm`, `erp`)
* `<entity>`: Exact table name from the source system

**Example**

```
crm_customer_info
```

Represents customer information ingested directly from the CRM system.

---

### 🔹 Silver Layer Rules

* Table names must retain the **source system prefix**.
* Entity names must remain unchanged from the Bronze layer.
* Data is cleaned and standardized, but naming remains consistent with the source.

**Pattern**

```
<sourcesystem>_<entity>
```

**Example**

```
crm_customer_info
```

Represents cleansed and standardized CRM customer data.

---

### 🔹 Gold Layer Rules

* Table names must use **business-aligned, meaningful names**.
* Names must start with a **category prefix** indicating the table type.
* This layer is designed for analytics and reporting.

**Pattern**

```
<category>_<entity>
```

* `<category>`: Role of the table (e.g., `dim`, `fact`)
* `<entity>`: Business entity name (e.g., `customers`, `products`, `sales`)

**Examples**

```
dim_customers
fact_sales
```

---

## 3️⃣ Glossary of Category Patterns

| Pattern | Meaning         | Examples                               |
| ------- | --------------- | -------------------------------------- |
| dim_    | Dimension table | dim_customers, dim_products            |
| fact_   | Fact table      | fact_sales                             |
| report_ | Reporting table | report_customers, report_sales_monthly |

---

## 4️⃣ Column Naming Conventions

### 🔹 Surrogate Keys

* All **dimension tables** must use surrogate keys.
* Surrogate keys must end with the suffix `_key`.

**Pattern**

```
<entity>_key
```

**Example**

```
customer_key
```

Surrogate key in the `dim_customers` table.

---

### 🔹 Technical Columns

* All system-generated metadata columns must start with the prefix `dwh_`.
* These columns are used for auditing, lineage, and load tracking.

**Pattern**

```
dwh_<column_name>
```

**Example**

```
dwh_load_date
```

Indicates the date when the record was loaded into the warehouse.

---

## 5️⃣ Stored Procedure Naming Conventions

* Stored procedures used for loading data must clearly indicate the layer they load.
* Procedure names must start with `load_` followed by the layer name.

**Pattern**

```
load_<layer>
```

* `<layer>`: Target data layer (`bronze`, `silver`, `gold`)

**Examples**

```
load_bronze
load_silver
load_gold
```

---

## ✅ Summary

Adhering to these naming conventions ensures:

* Clear separation of concerns across layers
* Improved collaboration between data engineers and analysts
* Easier maintenance and scalability of the data warehouse

These standards must be followed for all new development and enhancements.
