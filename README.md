# 🚀 Real-Time Ride Data Pipeline (Azure + Databricks)

## 📌 Overview:
This project implements an end-to-end Real-time data pipeline that ingests ride booking data from a custom web application, processes it using streaming architecture, and builds a Medallion Architecture (Bronze → Silver → Gold) using Azure and Databricks.

## 🧩 Architecture
🔄 Data Flow
Website → Event Hub → Dataricks [Bronze → Silver → Gold (Star Schema]


⚙️ Technologies Used
- Azure Event Hub (Kafka API)
- Azure Data Lake Storage (ADLS)
- Databricks (Delta Live Tables)
- PySpark (Structured Streaming)
- Delta Lake
- GitHub (Static Data Storage)

<img width="1536" height="1024" alt="1architecture" src="https://github.com/user-attachments/assets/ac9a731f-5dd7-41c8-be2b-6f8908c1ad72" />

