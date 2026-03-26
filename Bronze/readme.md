🥉 Bronze Layer – Data Ingestion
📌 Purpose

The Bronze layer ingests both real-time streaming data and batch/static data from multiple sources into the data lake.

🔹 Data Ingestion Methods:
* Real-time Streaming Data:
      1. Ride events stored in Azure Event Hub are ingested into Databricks using structured streaming.
      2. Data is stored as a streaming Delta table (rides_raw).
* Batch / Static Data:
      1. JSON files (bulk and mapping data) are pulled from GitHub using Azure Data Factory.
      2. Data is first stored in Azure Data Lake Storage and then ingested into Databricks as Delta tables.
