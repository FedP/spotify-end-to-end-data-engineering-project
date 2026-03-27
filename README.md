# Spotify-End-to-End-Data-Engineering-Project
Serverless ETL pipeline on AWS using Python.  Extracts data from Spotify API (Lambda + CloudWatch) Stores raw data in S3 Transforms data with Lambda (triggered by S3 events) Uses Glue + Athena for schema and querying  Tech stack: Python, AWS Lambda, S3, Glue, Athena, CloudWatch

## 📊 Project Overview

This project is a simple end-to-end **ETL data pipeline on AWS**, built with Python and fully serverless.

The pipeline extracts data from the Spotify API, processes it, and makes it queryable using SQL — all without managing any infrastructure.

---

## 🔹 Extract

- A Python script (running on AWS Lambda) pulls data from the Spotify API  
- Triggered daily using Amazon CloudWatch (scheduled event)  
- Handles API requests, pagination, and JSON responses  
- Raw data is stored in an Amazon S3 bucket (data lake - raw layer)  

---

## 🔹 Transform

- S3 `ObjectCreated` events trigger a second AWS Lambda function  
- Data processing includes:
  - Data cleaning (null handling, type casting)  
  - Schema normalization  
  - Flattening nested JSON structures  
  - Optional aggregation or filtering  
- Transformed data is written to a separate S3 bucket (processed layer)  
- Designed to be idempotent to avoid duplicate processing  

---

## 🔹 Load

- AWS Glue Crawler automatically scans the transformed data  
- Infers schema and updates the AWS Glue Data Catalog  
- Tables become immediately queryable via Amazon Athena  
- Athena enables serverless SQL queries directly on S3  

---

## ⚙️ Technical Highlights

- **Serverless architecture** → no infrastructure management  
- **Event-driven design** → S3 triggers automate processing  
- **Scalable** → Lambda and S3 scale automatically with data volume  
- **Data Lake structure** → separation between raw and transformed layers  
- **Schema-on-read** → flexible querying with Athena  
- **Cost-efficient** → pay-per-use model (Lambda, Athena, S3)  

---

## 🚀 Key Features

- Automated daily data ingestion  
- Real-time transformation on data arrival  
- Clean and analytics-ready datasets  
- SQL-based analytics without a database  
- Modular and extensible pipeline design  
