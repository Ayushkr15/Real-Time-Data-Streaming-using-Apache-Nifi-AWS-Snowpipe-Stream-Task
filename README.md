# Real-Time Data Streaming using Apache NiFi, AWS, Snowpipe, Stream & Task

![Screenshot 2025-02-20 203925](https://github.com/user-attachments/assets/34da0c9b-ab0d-4442-bc2b-d77c7f10f04d)


## 🚀 Project Overview
This project demonstrates a real-time data streaming pipeline using **Apache NiFi**, **AWS S3**, and **Snowflake** (with Snowpipe, Streams, and Tasks). It implements **Type 1 (SCD 1)** and **Type 2 (SCD 2)** Slowly Changing Dimensions to manage historical and current customer data efficiently. The workflow includes automated data ingestion, transformation, and loading into Snowflake with near-real-time updates.

## 🔧 Technologies Used
- **Cloud Services**: AWS S3 (Data Storage)
- **Data Pipeline**: Apache NiFi (Data Ingestion & Orchestration)
- **Data Warehouse**: Snowflake (Snowpipe, Streams, Tasks, Merge Operations)
- **Data Generation**: Python, Faker Library
- **Version Control**: GitHub

## 📂 Repository Structure
- `1. Table Creation.sql`: Creates Snowflake tables (`customer`, `customer_history`, `customer_raw`) and streams.
- `2. Data Loading.sql`: Configures AWS S3 external stage, file format, and Snowpipe for auto-ingestion.
- `3. SCD 1.sql`: Implements SCD Type 1 logic using MERGE statements and automated tasks.
- `4. SCD 2.sql`: Implements SCD Type 2 logic with historical tracking via streams and tasks.
- `Dataset Generation.ipynb`: Python script to generate synthetic customer data using Faker.

## 🛠️ Setup Instructions
1. **AWS S3 & Snowflake Integration**:
   - Create an S3 bucket and configure IAM credentials.
   - Set up an external stage in Snowflake pointing to your S3 bucket.
   - Create a Snowpipe for auto-ingesting data from S3.

2. **Snowflake Configuration**:
   - Run `1. Table Creation.sql` to create tables and streams.
   - Execute `2. Data Loading.sql` to set up the data ingestion pipeline.
   - Deploy SCD logic using `3. SCD 1.sql` and `4. SCD 2.sql`.

3. **Data Generation**:
   - Run the Jupyter notebook `Dataset Generation.ipynb` to generate CSV files.
   - Upload the CSV to your S3 bucket for Snowpipe ingestion.

4. **Automation**:
   - Schedule Snowflake tasks (`tsk_scd_raw` and `tsk_scd_hist`) to run every minute for real-time updates.

## 📊 Key Features
- **SCD Type 1**: Overwrites old data with new changes (e.g., email updates).
- **SCD Type 2**: Tracks historical changes with `start_time`, `end_time`, and `is_current` flags.
- **Real-Time Streaming**: Uses Snowpipe for automatic data loading and streams for change tracking.
- **Automated Workflows**: Tasks and stored procedures ensure seamless data synchronization.

## 📈 Results
- `customer` table holds the latest customer records.
- `customer_history` table maintains a full audit trail of changes.
- Streams (`customer_table_changes`) capture INSERT/UPDATE/DELETE operations in real time.
