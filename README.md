# Azure Data Factory: Blob CSV to Azure SQL Database Pipeline

## Overview
This project demonstrates an end-to-end Azure Data Engineering pipeline built using **Azure Data Factory (ADF)**, **Azure Blob Storage**, and **Azure SQL Database**.

The pipeline reads a CSV file from Azure Blob Storage and loads the data into an Azure SQL Database table using ADF Copy Activity. This project was built as hands-on practice for core Data Engineering concepts such as cloud storage, pipeline orchestration, linked services, datasets, and relational data loading.

---

## Architecture
**Source:** Azure Blob Storage (CSV file)  
**Orchestration:** Azure Data Factory  
**Target:** Azure SQL Database  

Flow:

`Azure Blob Storage CSV -> Azure Data Factory Copy Activity -> Azure SQL Database`

---

## Project Components

### 1. Azure Blob Storage
- Stores the source CSV file: `BigMart Sales.csv`
- Used as the raw input layer for the pipeline

### 2. Azure Data Factory
- Created linked services for:
  - Azure Blob Storage
  - Azure SQL Database
- Created datasets for:
  - Source CSV file
  - Target SQL table
- Built pipeline:
  - `PL_BLOB_CSV_AZ_SQL_DB`
- Copy activity:
  - `CPY-BLOB_CSV-SQL_DB`

### 3. Azure SQL Database
- Target table: `dbo.bigmart_sales`
- Stores the ingested CSV data for downstream querying and analysis

---

## Dataset Details

The source CSV contains BigMart sales-related data with the following columns:

- `Item_Identifier`
- `Item_Weight`
- `Item_Fat_Content`
- `Item_Visibility`
- `Item_Type`
- `Item_MRP`
- `Outlet_Identifier`
- `Outlet_Establishment_Year`
- `Outlet_Size`
- `Outlet_Location_Type`
- `Outlet_Type`
- `Item_Outlet_Sales`

---

## SQL Table Creation Script

```sql
CREATE TABLE dbo.bigmart_sales (
    Item_Identifier           VARCHAR(20),
    Item_Weight               DECIMAL(10,2),
    Item_Fat_Content          VARCHAR(50),
    Item_Visibility           DECIMAL(18,6),
    Item_Type                 VARCHAR(100),
    Item_MRP                  DECIMAL(10,4),
    Outlet_Identifier         VARCHAR(20),
    Outlet_Establishment_Year INT,
    Outlet_Size               VARCHAR(30),
    Outlet_Location_Type      VARCHAR(50),
    Outlet_Type               VARCHAR(50),
    Item_Outlet_Sales         DECIMAL(12,4)
);
```
## Pipeline Execution Result
The pipeline execution completed successfully and loaded the CSV data from Azure Blob Storage into Azure SQL Database.

### Load Summary
- **Rows loaded:** 8,523
- **Source:** Azure Blob Storage
- **Sink:** Azure SQL Database
- **Execution type:** Copy Activity

---

## Skills Demonstrated
- Azure Data Factory pipeline creation
- Azure Blob Storage integration
- Azure SQL Database integration
- Linked services and datasets
- CSV to SQL data loading
- Schema mapping
- Basic cloud data ingestion pipeline design
- Monitoring pipeline runs

---

## Project Structure

```bash
├── README.md
├── ARMTemplateForFactory.json
├── ARMTemplateParametersForFactory.json
├── screenshots/
│   └── pipeline-run-success.png
└── data/
    └── BigMart Sales.csv
```
## How to Run
1. Upload the source CSV file to Azure Blob Storage.
2. Create the target table in Azure SQL Database.
3. Create linked services in Azure Data Factory for Blob Storage and Azure SQL Database.
4. Create source and sink datasets.
5. Build the Copy Activity pipeline.
6. Debug or trigger the pipeline.

## Learning Outcome

This project helped me understand how to build a basic yet practical Azure ETL pipeline using managed Azure services. It strengthened my understanding of how data moves from raw cloud storage into a structured relational database through orchestration in Azure Data Factory.
