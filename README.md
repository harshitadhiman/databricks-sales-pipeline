**Sales Data Pipeline — Databricks + CI/CD
**
An end-to-end data engineering pipeline implementing the medallion architecture (Bronze → Silver → Gold) in Databricks, with automated deployment via GitHub Actions.

Architecture

``
Source Data → Bronze Layer → Silver Layer → Data Quality Checks → Gold Layer → Analytics
`

Tech Stack: Databricks (PySpark, Delta Lake) · GitHub Actions · Python · SQL

Project Structure

`
databricks-sales-pipeline/
├── Notebooks/
│   ├── Ingest Data - Bronze layer.ipynb
│   ├── Transformation and cleaning - Silver Layer.ipynb
│   ├── Data Quality Checks.ipynb
│   ├── Tables - fact & dimension.ipynb
│   └── Aggregate Tables - Gold Layer.ipynb
├── job/
│   └── jobs.json
├── .github/workflows/
│   └── main.yml
└── README.md
`

Pipeline Layers
Bronze (Ingestion)
Raw data ingested into Delta tables with minimal transformation.

Silver (Transformation)
• Null handling and type casting
• Feature engineering (deliverydays, deliverytype)
• Data standardization

Data Quality
• Null and duplicate checks
• Validation rules with pass/fail reporting

Gold (Analytics)
Aggregated tables for business metrics:
• Sales trends and regional analysis
• Customer behavior segmentation
• Delivery performance tracking

Data Model

| Fact Table | Dimension Tables |
|------------|------------------|
| Sales metrics (Sales, Quantity, Profit) | Customer, Product, Geography, Date |

CI/CD Pipeline

Triggered on every push to main:

Checkout repository
Install and authenticate Databricks CLI
Deploy notebooks to workspace
Update job configuration
Trigger pipeline run

Required Secrets: DATABRICKSHOST, DATABRICKSTOKEN`

Roadmap
• Incremental loading with MERGE
• Partition optimization
• Logging and monitoring layer
• BI tool integration (Power BI / Tableau)

Author
Harshita Dhiman — Data Engineering Enthusiast
