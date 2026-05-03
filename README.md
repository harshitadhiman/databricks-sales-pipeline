# 🚀 Sales Data Pipeline using Databricks with CI/CD Integration

---

## 📌 1. Project Overview

This project implements an **end-to-end data engineering pipeline** using Databricks, following the **Medallion Architecture (Bronze → Silver → Gold)**.

The pipeline ingests raw sales data, performs cleaning and transformations, applies data quality validations, and produces analytics-ready datasets. The entire workflow is automated using **CI/CD with GitHub Actions**.

---

## 📊 2. Dataset Description

The dataset represents **retail sales transactions**, containing:

* Order details (Order ID, Order Date, Ship Date)
* Customer information (Customer ID, Segment, Region)
* Product details (Category, Sub-category)
* Sales metrics (Sales, Quantity, Discount, Profit)

### 🧾 Bronze Layer Schema

```markdown
![Bronze Schema](images/bronze_schema.png)
```

---

## 🏗️ 3. Architecture

```text
Source Data → Bronze Layer → Silver Layer → Data Quality Checks → Gold Layer → Dashboard
```

---

## ⚙️ 4. Technology Stack

* Databricks (PySpark, Delta Lake)
* Python
* SQL
* GitHub (Version Control)
* GitHub Actions (CI/CD)
* Data Engineering Concepts (ETL, Data Modeling)

---

## 📂 5. Project Structure

```
databricks-sales-pipeline/
│
├── Notebooks/
│   ├── Ingest Data - Bronze layer.ipynb
│   ├── Transformation and cleaning - Silver Layer.ipynb
│   ├── Data Quality Checks.ipynb
│   ├── Tables - fact & dimension.ipynb
│   └── Aggregate Tables - Gold Layer.ipynb
│
├── job/
│   └── jobs.json
│
├── .github/workflows/
│   └── main.yml
│
└── README.md
```

---

## 🔄 6. End-to-End Pipeline Flow

### Step 1: Data Ingestion (Bronze Layer)

* Raw data is loaded into Delta tables
* No heavy transformation applied
* Serves as the source of truth

---

### Step 2: Data Transformation (Silver Layer)

* Data cleaning and preprocessing
* Schema standardization
* Derived columns added:

  * `delivery_days`
  * `delivery_type` (1-day, fast, delayed)

---

### Step 3: Data Quality Checks

* Validation rules applied on both Bronze and Silver layers
* Ensures reliability before downstream usage

---

### Step 4: Data Modeling

* Creation of Fact and Dimension tables
* Enables structured analytics

---

### Step 5: Gold Layer (Analytics)

* Aggregated tables for reporting
* Business insights generation

---

## 🔁 7. Workflow Pipeline (Databricks Jobs)

The pipeline is orchestrated using a **multi-task workflow**:

```
Bronze → Silver → Data Quality → Tables → Gold
```

### 📌 Workflow Execution

```markdown
![Workflow](images/pipeline.png)
```

---

## 🧪 8. Data Quality Framework

A dedicated data quality layer is implemented with **pass/fail logic** on both raw data(bronze_layer) and cleaned data (silver_layer).

### ✔ Checks Performed

* Null checks (Order ID, Customer ID)
* Duplicate detection
* Negative values validation
* Invalid discount values
* Invalid delivery calculations

---

### 📊 Data Quality Dashboard


```markdown
![Data Quality Dashboard](images/data_quality.png)
```

### 🧠 Key Observations

* Duplicate records detected in raw data and handled during cleaning
* All checks passed in cleaned dataset
* Data consistency improved after transformations

---

## 🔧 9. Transformations Applied

* Removed duplicate records
* Handled null values
* Standardized date formats
* Derived delivery metrics
* Validated business rules

---

## 📊 10. Data Model

### Fact Table

* Sales metrics: Sales, Quantity, Profit

### Dimension Tables

* Customer
* Product
* Geography
* Date

---

## 📈 11. Analytics & Use Cases

The Gold layer supports:

* Sales trend analysis (monthly/yearly)
* Customer behavior tracking
* Region-wise performance
* Delivery performance insights

---

## ⚡ 12. CI/CD Implementation

### Trigger

* Executes on every push to `main` branch

### Flow

1. Code pushed to GitHub
2. CI/CD pipeline triggered
3. Databricks CLI configured using secrets
4. Notebooks deployed to workspace
5. Existing job updated
6. Pipeline executed after deployment

---

## 🔐 13. GitHub Secrets

* `DATABRICKS_HOST`
* `DATABRICKS_TOKEN`

---

## 🛠️ 14. Skills Demonstrated

* Data Engineering (ETL Pipeline Design)
* PySpark Transformations
* Data Modeling (Fact & Dimension Tables)
* Data Quality Validation
* Workflow Orchestration
* CI/CD Implementation
* Git & Version Control
* Problem Solving & Debugging

---

## ▶️ 15. How to Run

1. Clone the repository
2. Import notebooks into Databricks (or use CI/CD)
3. Configure Databricks credentials
4. Run the workflow job
5. Validate outputs in Gold layer

---

## 🚀 16. Future Enhancements

* Incremental loading using MERGE
* Partitioning optimization
* Monitoring & logging layer
* Integration with BI tools (Power BI)
* Data Visualization with Aggregate Tables*

---

## 📌 17. Conclusion

This project demonstrates a **complete real-world data pipeline**, with Data ingestion, transformation, validation, orchestration, and deployment.

---

