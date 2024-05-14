---
layout: article
title: "Data Engineer: Data Warehouse & Store Procedure"
share: true
modified: 2017-02-12T14:18:57-04:00
image:
    teaser: idx_partners.png
categories: portofolio
---

*A project aimed to create a data warehouse schema and store procedures to streamline a company's data workflow.*

<strong>Author: Jesslyn Jane</strong>. This is a project I have worked through as part of the Virtual Internship final project at [ID/X Partners, Rakamin Academy](https://www.rakamin.com/virtual-internship-experience/data-engineer-id-x-partners).

[Github](https://github.com/jesslynnjane/ID-X_Data_Engineer?tab=readme-ov-file#1-data-warehouse-creation) \| [PPT](https://drive.google.com/file/d/1eZDgUgX2j5LzYxUypwYbV_yE7xmZ7328/view?usp=sharing) \| [Video PPT](https://drive.google.com/file/d/1XNd25OtA1SDWuTOU_T_FsI-xfGocxehU/view?usp=sharing)


## About Company
Established in 2002, ID/X Partners (PT IDX Consulting) has been catering to businesses across Asia and Australia, spanning diverse sectors including financial services, telecommunications, manufacturing, and retail. Specializing in Data Analytic and Decisioning (DAD) solutions, complemented by risk management and integrated marketing expertise, ID/X Partners assists clients in optimizing portfolio profitability and streamlining business processes. With its comprehensive consulting services and technological solutions, ID/X Partners stands out as a one-stop service provider.


## Background
One of the clients of ID/X Partners operating in the banking industry has a need to establish a Data Warehouse from multiple data sources stored within their systems.

## Available Data
The various data sources include:
- transaction_excel (Excel file)
- transaction_csv (CSV file)
- transaction_db (SQL Server Database)
- account (SQL Server Database)
- customer (SQL Server Database)
- branch (SQL Server Database)
- city (SQL Server Database)
- state (SQL Server Database)

## Problem Statement
The current challenge they face is difficulty in extracting data from various sources (Excel, CSV, databases) simultaneously, resulting in delays in their data reporting and analysis processes.


### 1. Data Warehouse Creation
Data warehouse consolidates information from several sources into a single comprehensive database. By aggregating all of this data in one location, the company may conduct a more comprehensive analysis of its customers. Assessing data collected from many diverse sources might give insight into a company's performance


![Data Warehouse](/images/data_warehouse.PNG)

Work Step: Create 3 dimension tables and 1 fact tables

![Create Table](/images/create_table.PNG)

### 2. Create ETL Job for Dimension Table
![ETL Dimension Table](/images/etl_job.PNG)

Explanations:
* 1 – **Job Designs:** data integration workflows created using Talend Studio, defining the flow of data processing tasks.

* 2 – **DB Connections:** store and manage relational database connections centrally, enabling reuse across multiple jobs for consistency.
* 3 – **File Delimited:** settings for delimited files (e.g., CSV) in the repository, streamlining file handling in Talend jobs.
* 4 – **File Excel:** store metadata settings for Excel files in the repository, simplifying integration of Excel data into Talend jobs.

Work Step:
![Work Step 1](/images/work_step_1.PNG)
![Work Step 2](/images/work_step_2.PNG)

### 3. Create ETL Job for Fact Table
![ETL Facct Table](/images/etl_job_2.PNG)

### 4. Create Store Procedure

There are 2 SP created:
- **DailyTransaction:** to calculate the number of transactions along with their total amounts for each day.
![DailyTransaction SP](/images/sp_1.PNG)

- **BalancePerCustomer:** calculate the remaining balance per customer.
![BalancePerCustomer SP](/images/sp2.PNG)


[Github](https://github.com/jesslynnjane/ID-X_Data_Engineer?tab=readme-ov-file#1-data-warehouse-creation) \| [PPT](https://drive.google.com/file/d/1eZDgUgX2j5LzYxUypwYbV_yE7xmZ7328/view?usp=sharing) \| [Video PPT](https://drive.google.com/file/d/1XNd25OtA1SDWuTOU_T_FsI-xfGocxehU/view?usp=sharing)