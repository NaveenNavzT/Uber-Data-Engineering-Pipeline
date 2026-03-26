## 🥇 Gold Layer – Data Warehouse (Star Schema with CDC)

### 📌 Purpose  
The Gold layer provides **analytics-ready data** by transforming the enriched Silver layer into a **Star Schema model** using streaming pipelines. It supports efficient querying, reporting, and business insights.

---

## ⭐ Architecture Overview  

- Source: `silver_obt` (enriched streaming table)  
- Output:
  - 1 Fact Table  
  - 6 Dimension Tables  
- Built using Delta Live Tables (DLT) with Change Data Capture (CDC)

---

## 🔷 Dimension Tables  

### 🔹 SCD Type 1 Dimensions (No History Tracking)

The following dimension tables are implemented using **Slowly Changing Dimension Type 1**, where updates overwrite existing records:

- `dim_passenger`  
  - passenger details (name, email, phone)

- `dim_driver`  
  - driver details (name, rating, phone, license)

- `dim_vehicle`  
  - vehicle attributes (type, make, model, color)

- `dim_payment`  
  - payment details (method, card flag, authentication)

- `dim_booking`  
  - booking-level details (timestamps, locations, ride status)

🔶 Dimension Table – SCD Type 2
#dim_location
#📌 Purpose:

- Tracks historical changes in location attributes.

⭐ Fact Table – fact
#📌 Purpose:

- Stores ride-level transactional data for analytical queries.

🔄 CDC Implementation

All Gold tables are built using:

dp.create_auto_cdc_flow()
Benefits:
Incremental data processing
Handles inserts and updates efficiently
Supports both SCD Type 1 and Type 2

🔗 Data Flow

- silver_obt → Dimension Tables + Fact Table → Analytics / BI

📊 Use Cases
- Ride volume analysis
- Revenue and fare breakdown
- Driver and passenger insights
- Payment method trends
- Location-based analytics

🎯 Key Features
- Streaming Star Schema implementation
- Real-time dimension and fact table updates
- SCD Type 1 and Type 2 modeling
- CDC-based incremental processing
- Scalable and analytics-ready design

🧠 Summary
- Table Type	Tables Count	Description
- Fact Table	1	Ride-level metrics
- Dimensions	5 (SCD1) + 1 (SCD2)	Descriptive attributes
- Processing	Streaming + CDC	Incremental updates


🚀 Conclusion

The Gold layer transforms streaming data into a structured data warehouse model, enabling efficient analytics and real-time business insights.
