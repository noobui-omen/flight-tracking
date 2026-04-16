# Real-Time Flight Tracking & Delay Risk System

## Overview

This project implements a real-time aviation analytics pipeline that ingests live aircraft state data, computes airport-level congestion metrics, and generates delay risk scores using streaming data processing.

The system is designed to demonstrate end-to-end real-time data engineering using Kafka and Spark Structured Streaming.

---

## Architecture

**Data Flow:**

OpenSky API → Kafka (Ingestion) → Spark Structured Streaming → Storage → Dashboard

**Components:**

* Data Ingestion: Python service polling OpenSky API
* Messaging Layer: Apache Kafka
* Stream Processing: PySpark (Structured Streaming)
* Storage: (PostgreSQL / Parquet / Elastic - depending on your implementation)
* Visualization: (Streamlit / Dashboard)

---

## Features

* Real-time ingestion of live flight data
* Airport-level congestion metrics:

  * Aircraft count per airport
  * Percentage of aircraft on ground
  * Average velocity near airport
* Delay risk scoring based on real-time features
* Streaming pipeline with continuous processing
* Dashboard for monitoring live system state

---

## Tech Stack

* Python
* Apache Kafka
* PySpark (Structured Streaming)
* OpenSky API
* (Optional: PostgreSQL / Elasticsearch / Streamlit)

---

## Project Structure

```
.
├── ingestion/
│   └── opensky_producer.py
├── streaming/
│   └── spark_streaming.py
├── models/
│   └── delay_model.py
├── dashboard/
│   └── app.py
├── data/
├── README.md
```

---

## How to Run

### 1. Start Kafka

Ensure Kafka and Zookeeper are running.

### 2. Run Ingestion Service

```
python ingestion/opensky_producer.py
```

### 3. Start Streaming Job

```
spark-submit streaming/spark_streaming.py
```

### 4. Launch Dashboard

```
python dashboard/app.py
```

---

## Delay Risk Logic

A simple real-time delay risk score is computed using:

* Aircraft density near airport
* Percentage of aircraft on ground
* Average velocity trends

This provides a proxy for congestion and potential delays.

---

## Data Sources

* OpenSky Network API (live flight data)
* BTS (Bureau of Transportation Statistics) – historical delay data (optional for model training)
* FAA Airport Status (optional enrichment)

---

## Limitations

* Delay prediction is based on proxy features, not airline schedules
* API rate limits may affect ingestion frequency
* System focuses on airport-level insights rather than individual flight prediction

---

## Future Improvements

* Integrate weather data for improved delay prediction
* Add historical model training pipeline
* Enhance geospatial accuracy for airport mapping
* Improve dashboard interactivity

---

## Contributors

* [Your Name]
* [Team Member 2]
* [Team Member 3]
* [Team Member 4]
