E-Commerce Data Engineering Project using Medallion Architecture
Overview
This project implements an end-to-end data engineering pipeline using the Medallion Architecture (Bronze, Silver, Gold) on Databricks. The pipeline processes raw e-commerce data, performs data cleaning and transformation, and generates business-ready insights through KPIs.

Architecture
Bronze Layer
Raw data ingestion from Amazon S3
Data stored in Delta tables without any transformation
Schema inference avoided to maintain consistency
Silver Layer
Data cleaning and preprocessing
Removal of duplicates
Handling of missing values
Standardization of data types and timestamps
Referential integrity checks across datasets
Gold Layer
Implementation of star schema
Creation of dimension and fact tables
Construction of curated dataset for analytics
KPI computation and storage as Delta tables
Data Flow
S3 → Bronze → Silver → Gold → KPI Analysis

Gold Layer Design
Dimension Tables
dim_customer
dim_product
dim_seller
dim_date
Fact Tables
fact_orders
fact_order_items
fact_payments
fact_reviews
Curated Dataset
Built at order-item level
Ensures no duplication using proper aggregation
Serves as the single source for KPI computation
KPIs Implemented
Total revenue by month
Average Order Value (AOV)
Top 10 products by revenue
Top 10 sellers by revenue
Orders by customer city and state
New vs returning customers (monthly)
Customer Lifetime Value (CLV)
Order fulfillment rate
Late delivery percentage
Average delivery time (days)
Payment method distribution
Average review score by product category
Average review score by seller
Percentage of low-rated orders (rating < 3)
Advanced Analytics
Data Cube implemented using GROUP BY CUBE

Enables multi-dimensional aggregation across:

Time (year, month)
Geography (state)
Product category
Pipeline Orchestration
Implemented using Databricks Jobs

Task-based execution with dependencies:

Bronze → Silver → Gold → KPI
Ensures automated and sequential data processing

Repository Structure
de-mini-project/ │ ├── 01_notebooks/ │ ├── bronze_layer │ ├── silver_layer │ ├── gold_layer │ └── gold_kpi_analysis │ ├── 04_pipeline/ │ └── pipeline.png │ ├── 05_documentation/ │ └── README.md

Technologies Used
Apache Spark (PySpark)
Databricks
Delta Lake
SQL
Amazon S3
Key Highlights
No schema inference in Bronze layer
Robust data cleaning in Silver layer
Proper grain handling to avoid duplication
Accurate KPI computation using curated dataset
Use of aggregation and partitioning for performance optimization
End-to-end pipeline orchestration using Databricks Jobs
Conclusion
This project demonstrates a complete data engineering workflow from raw data ingestion to business insights. It follows industry best practices in data modeling, transformation, and analytics using scalable big data technologies.
