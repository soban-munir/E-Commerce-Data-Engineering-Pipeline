# E-Commerce Data Engineering Pipeline (Medallion Architecture)

## Project Objective & Problem Statement

In modern e-commerce environments, data is often siloed across different platforms:
- Transactional data resides in SQL databases  
- Customer metadata exists in static CSV files  
- Real-time user information is exposed via REST APIs  

### The Problem

Business stakeholders cannot obtain a clear **"Customer 360" view** because:

- Data is disconnected across systems  
- It is uncleaned and inconsistent  
- Business logic is not applied  
- No centralized analytics layer exists  

### The Solution
This project implements an **automated Data Engineering Pipeline** using the **Medallion Architecture (Bronze → Silver → Gold)** on Azure.

The pipeline:

- Ingests fragmented data from multiple sources  
- Cleans and integrates data in the Silver layer  
- Applies business logic in the Gold layer  

# Project Overview

This repository contains a production-grade data engineering pipeline built on **Azure Databricks using PySpark**.

It demonstrates end-to-end transformation of raw, disconnected data sources into a high-value **Gold analytics layer** optimized for BI reporting.

# Tech Stack

| Component | Technology Used |
|------------|----------------|
| Orchestration | Azure Data Factory (ADF) |
| Processing Engine | Azure Databricks (Spark SQL & PySpark) |
| Data Lake | Delta Lake |
| Governance | Unity Catalog |
| Data Sources | REST API (JSON), CSV Files |


# Data Pipeline Architecture

## 🟤 1. Bronze Layer – Raw Ingestion

The Bronze layer stores data in its rawest form to preserve the original source records.

### Key Activities:
- Automated ingestion of:
  - CSV files
  - REST API JSON responses
- Stored as **Delta Tables**

## ⚪ 2. Silver Layer – Cleanse & Integration

This layer ensures data quality and builds a **Unified Customer 360 View**.

### Transformations Performed:

- **Data Flattening**
  - Extracted nested JSON from REST API into relational structure  

- **Standardization**
  - Lowercased email addresses  
  - Standardized phone number formats  
  - Handled null/missing values  

- **Identity Resolution**
  - Complex joins between API data and CRM CSVs  
  - Custom ID mapping logic to unify disparate datasets  


## 🟡 3. Gold Layer – Business Logic & Aggregations

The Gold layer transforms curated data into business-ready analytics tables.

### Business Outputs:

### Customer Segmentation
Users categorized into:
- Platinum
- Gold
- Silver  

Based on **Total Lifetime Spend**

### Sales Performance Metrics
- Monthly Revenue Trends  
- Country-wise Sales Performance  
- Pre-calculated KPIs for BI tools (Power BI optimized)


# Analytical Impact

This pipeline enables stakeholders to answer critical business questions:

- Who are our most valuable customers?
- Which regions are driving growth?
- What is our revenue growth rate?
- How is monthly performance trending?


#  Key Engineering Features

###  Scalability
Designed using Spark’s distributed processing to handle increasing transactional volumes.

###  Reliability
Implemented:
- Overwrite logic
- Merge (Upsert) operations  
To maintain data consistency.

###  Schema Evolution
Leveraged Delta Lake to automatically manage evolving data schemas.

###  BI Optimization
Gold layer designed for fast dashboard performance in Power BI.


#  Author

**Soban Munir**  
Data Engineer | Computer Science Student  

LinkedIn: www.linkedin.com/in/soban-munir-89b64b333  
Portfolio: https://soban-munir-portfolio.vercel.app/  


> ⭐ If you found this project useful, feel free to star the repository!
