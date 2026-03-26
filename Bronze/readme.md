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

<img width="1072" height="802" alt="2Bronze1" src="https://github.com/user-attachments/assets/a3729047-769e-4bab-8fd6-360ad0e4a4ba" />

<img width="804" height="600" alt="3Bronze2" src="https://github.com/user-attachments/assets/12ec51c0-41aa-4f55-a2bc-c7cdb9cf0ffc" />

<img width="725" height="862" alt="4Bronze3" src="https://github.com/user-attachments/assets/4c079691-591c-4d03-8c6b-3decf8030d50" />

<img width="733" height="678" alt="5Bronze4" src="https://github.com/user-attachments/assets/4a204fff-a9b4-476f-b63d-57ed89b10705" />




