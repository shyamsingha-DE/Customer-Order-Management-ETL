Customer & Order Management ETL Pipeline
PySpark | Delta Lake | Data Quality | Bronze → Silver → Gold

An end-to-end ETL pipeline for processing customer and order data using PySpark and Delta Lake.

The project demonstrates data ingestion, cleansing, validation, referential integrity checks, business-rule transformations, customer-level aggregations, and Delta Lake persistence.

📌 Project Overview

The pipeline processes messy customer and order data through a Bronze → Silver → Gold architecture.

The objective is to transform raw operational data into clean, validated, and analytics-ready datasets while implementing data-quality controls throughout the pipeline.

Architecture
Raw Customer Data ──→ Bronze Customers ──→ Silver Customers ──┐ │ ├──→ Gold Customer Sales Summary │ Raw Order Data ──────→ Bronze Orders ──────→ Silver Orders ────┘

🏗️ Data Layers
Bronze Layer

The Bronze layer stores the raw source data in Delta format with minimal transformation.

Customers

Customer_ID
Customer_Name
Email
Phone
City
Registration_Date

Orders

Order_ID
Customer_ID
Order_Date
Product
Quantity
Unit_Price
Order_Status
Silver Layer

The Silver layer performs data cleansing, standardization, and validation.

Customer transformations
Customer ID standardization and validation
Customer name trimming and capitalization
Whitespace normalization
Email standardization and validation
Phone number normalization and validation
City standardization
Registration date parsing
Invalid values converted to NULL
Original raw values preserved for data-quality investigation
Order transformations
Order ID standardization and validation
Customer ID standardization and validation
Order date parsing
Product standardization
Quantity validation
Unit price cleaning and numeric conversion
Order status standardization and validation
Invalid values converted to NULL
Original raw values preserved
🔍 Data Quality Validation

The project includes multiple validation checks across the Silver and Gold layers.

Silver validations
Record-count validation
Duplicate ID detection
Field-level validation
Invalid-value detection
Invalid → NULL verification
Referential integrity validation
Raw-value preservation checks
Gold validations
Customer coverage
Cancelled-order exclusion
Calculation accuracy
Zero-order customer handling
Metric consistency
Negative metric detection
Source-to-Gold reconciliation

These validations demonstrate how data-quality controls can be incorporated directly into an ETL pipeline rather than treating validation as a separate activity.

📊 Gold Layer

The Gold layer produces a customer-level sales summary.

Metrics
Column	Description
Customer_ID	Customer identifier
Customer_Name	Customer name
City	Customer city
Registration_Date	Customer registration date
Number_of_Orders	Number of qualifying orders
Total_Amount	Total order value
Average_Order_Amount	Average order value
Total_Quantity	Total quantity purchased

Cancelled orders are excluded from the business metrics, while customers without qualifying orders are retained with zero-valued metrics.

🛠️ Technologies
Python
PySpark
Apache Spark
Delta Lake
Spark SQL
Databricks / Spark environment
SQL

📂 Project Structure
Customer-Order-Management-ETL/
│
├── Customer_Order_Management_ETL.ipynb
├── README.md
├── requirements.txt
│
├── data/
│   └── README.md
│
└── screenshots/
    └── README.md

🚀 Key PySpark Concepts Demonstrated
DataFrame transformations
withColumn()
when() / otherwise()
regexp_replace()
rlike()
try_cast()
try_to_timestamp()
trim()
upper() / lower() / initcap()
coalesce()
join()
left_anti joins
groupBy() / agg()
sum() / avg() / count()
Duplicate detection
Delta Lake read/write
Delta persistence and read-back verification

🎯 Business Value

This pipeline demonstrates how raw operational data can be transformed into reliable, analytics-ready information.

The project focuses not only on transformation but also on data quality, validation, traceability, and business-rule enforcement, which are important aspects of production data engineering.

📚 Learning Outcomes

Through this project, I practiced:

Designing a Bronze → Silver → Gold ETL architecture
Building reusable PySpark transformation logic
Handling messy real-world-style data
Implementing field-level data-quality rules
Preserving raw values for investigation
Validating relationships between datasets
Building customer-level analytical aggregates
Persisting datasets using Delta Lake
Performing post-write verification

👨‍💻 Author

Shyam Singha

QA Lead / Testing Professional transitioning into Data Engineering and Analytics.

Focus Areas

PySpark • Databricks • SQL • Data Quality • Data Engineering • Power BI

📌 Note

This project uses intentionally messy sample data to demonstrate data cleansing, validation, and ETL design patterns.
