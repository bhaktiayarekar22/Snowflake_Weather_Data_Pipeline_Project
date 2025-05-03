# ❄️ Snowflake Weather Data Pipeline Project

## 📌 Project Overview

This project showcases a real-time data pipeline that fetches weather data from an external API, stores it in AWS DynamoDB, transfers it to Amazon S3, and automatically ingests it into Snowflake using Snowpipe for further analysis.

---

## 💡 Problem Statement

Access to real-time, structured weather data across multiple Indian cities is often limited or unorganized. Businesses and researchers need this data to make informed decisions, whether for logistics, agriculture, travel, or predictive modeling. The challenge lies in:

- Automatically gathering real-time data from an external API
- Structuring and storing the data efficiently
- Automating the data transfer to a cloud data warehouse (Snowflake)
- Making the data ready for querying and visualization with minimal latency

---

## 🔁 Project Flow

1. **Data Ingestion via Lambda 1**
   - AWS Lambda periodically fetches real-time weather data for 10 Indian cities from `weatherapi.com`.
   - The data includes temperature, humidity, pressure, wind speed and direction, etc.
   - The data is stored in a DynamoDB table (`weather`).

2. **Stream Processing via Lambda 2**
   - A DynamoDB Stream captures new entries.
   - A second AWS Lambda function processes the stream, formats the data into CSV, and uploads it to an S3 bucket.

3. **Storage and Ingestion**
   - The CSV files are stored in an Amazon S3 bucket (`snowflake-project-2-weather/snowflake/`).
   - Snowflake uses Snowpipe and a storage integration to automatically detect and ingest new files into a Snowflake table.

4. **Data Access**
   - The data is now available in Snowflake for querying, visualization, and reporting.

---

## 📊 Result

- Real-time weather data for 10 cities is successfully fetched, transformed, and stored in Snowflake with near real-time ingestion.
- The system can scale to more cities or frequency with minimal changes.
- Data in Snowflake can be used for analytics dashboards, time-series forecasting, anomaly detection, and reporting.

---

## 🌐 Technologies Used

- **AWS Lambda** for serverless execution
- **Amazon DynamoDB** for real-time data storage
- **Amazon S3** for durable object storage
- **Snowflake** for scalable cloud-based analytics
- **Snowpipe** for automated ingestion from S3
- **EventBridge** for scheduling Lambda executions
- **WeatherAPI** for public weather data

---

## 🧾 Summary

This project demonstrates a complete real-time data engineering workflow using serverless architecture and cloud-native tools. It highlights how AWS and Snowflake can be integrated seamlessly to build scalable, automated pipelines for external data ingestion and analytics.

