
---

# 📊 Sales Data Pipeline — Databricks + CI/CD

An end-to-end data engineering pipeline implementing the **Medallion Architecture (Bronze → Silver → Gold)** using Databricks. The project includes automated deployment and orchestration through GitHub Actions for a fully CI/CD-enabled workflow.

---

## 🚀 Overview

This project demonstrates how to design and build a scalable data pipeline that:

* Ingests raw data into Delta Lake
* Transforms and cleans data for analytics
* Applies data quality checks
* Produces business-ready aggregated datasets
* Automates deployment using CI/CD

---

## 🏗️ Architecture

```
Source Data → Bronze → Silver → Data Quality → Gold → Analytics
```

---

## 🛠️ Tech Stack

* **Databricks** (PySpark, Delta Lake)
* **Python**
* **SQL**
* **GitHub Actions** (CI/CD)

---

## 📁 Project Structure

```
databricks-sales-pipeline/
├── Notebooks/
│   ├── Ingest Data - Bronze Layer.ipynb
│   ├── Transformation & Cleaning - Silver Layer.ipynb
│   ├── Data Quality Checks.ipynb
│   ├── Fact & Dimension Tables.ipynb
│   └── Aggregations - Gold Layer.ipynb
├── job/
│   └── jobs.json
├── .github/workflows/
│   └── main.yml
└── README.md
```

---

## 🔄 Pipeline Layers

### 🟫 Bronze (Ingestion)

* Raw data ingestion into Delta tables
* Minimal transformations to preserve source data

### ⚪ Silver (Transformation)

* Null handling and type casting
* Data cleaning and standardization
* Feature engineering (`delivery_days`, `delivery_type`)

### ✅ Data Quality

* Null and duplicate checks
* Business rule validation with pass/fail reporting

### 🟨 Gold (Analytics)

* Aggregated datasets for reporting and insights:

  * Sales trends
  * Regional performance
  * Customer segmentation
  * Delivery efficiency

---

## 📊 Data Model

| Fact Table                      | Dimension Tables                   |
| ------------------------------- | ---------------------------------- |
| Sales (Sales, Quantity, Profit) | Customer, Product, Geography, Date |

---

## ⚙️ CI/CD Pipeline

Automated using GitHub Actions and triggered on every push to `main`.

### Workflow Steps:

1. Checkout repository
2. Install and authenticate Databricks CLI
3. Deploy notebooks to Databricks workspace
4. Update job configuration
5. Trigger pipeline run

### 🔐 Required Secrets

* `DATABRICKS_HOST`
* `DATABRICKS_TOKEN`

---



