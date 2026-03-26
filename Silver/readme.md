## 🥈 Silver Layer – Data Transformation & Enrichment  

### 📌 Purpose  
The Silver layer is responsible for **cleaning, standardizing, and enriching** the raw data from the Bronze layer. It combines both streaming and batch data to produce a structured and analytics-ready dataset.

---

## 🔹 Pipeline 1: `silver.py` (Data Standardization)

### 📌 Description  
This pipeline processes both **bulk (historical)** and **real-time streaming** data and loads them into a unified staging table: `stg_rides`.

### ⚙️ Key Steps  

- **Schema Definition**  
  - A predefined schema (`rides_schema`) is used to parse incoming JSON data from the streaming source.

- **Streaming Table Creation**  
  - A streaming table `stg_rides` is created to store processed data.

- **Bulk Data Ingestion**  
  - Historical data (`bulk_rides`) is ingested using streaming read  
  - Timestamp columns are properly cast for consistency  

- **Streaming Data Ingestion**  
  - Real-time data from `rides_raw` is parsed using `from_json()`  
  - Extracted fields are flattened into structured columns  

### ✅ Output  
- Unified staging table: `stg_rides`  
- Contains both historical and real-time ride data  

---

## 🔹 Pipeline 2: `silver_obt.sql` (Data Enrichment)

### 📌 Description  
This pipeline enriches the staging data by joining it with multiple dimension (mapping) tables to create a **denormalized, business-ready dataset**.

### ⚙️ Key Transformations  

- Reads streaming data from:
  - `stg_rides`

- Applies:
  - Data enrichment using LEFT JOINs with mapping tables:
    - vehicle makes  
    - vehicle types  
    - ride statuses  
    - payment methods  
    - cities  
    - cancellation reasons  

- Adds:
  - Descriptive attributes (e.g., vehicle type, payment method, city details)

- Uses:
  - **Watermarking** on `booking_timestamp` to handle late-arriving data  

---

## 🔗 Data Enrichment Example  

- `vehicle_type_id` → vehicle details  
- `payment_method_id` → payment info  
- `pickup_city_id` → city, state, region  
- `ride_status_id` → ride status description  

---

## 📊 Output Table  

- Final enriched streaming table:
  - `silver_obt`

---

## 🎯 Key Features  

- Combines **batch + streaming data** into a unified dataset  
- Performs **real-time enrichment using dimension tables**  
- Handles **late-arriving data using watermarking**  
- Produces a **clean, denormalized dataset** for downstream processing  

---

## 🧠 Summary  

| Pipeline        | Purpose                     | Output        |
|----------------|----------------------------|---------------|
| `silver.py`    | Data cleaning & standardization | `stg_rides`   |
| `silver_obt.sql` | Data enrichment & joins     | `silver_obt`  |
