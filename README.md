# retail_deltashare

# Synthetic Retail Data Engineering Pipeline (Databricks)

## Project Overview

Built an end-to-end **batch + streaming retail data pipeline** using **Databricks, PySpark, Delta Lake, and Auto Loader**, based on Databricks’ synthetic retail dataset.
The project focuses on **standardizing messy raw data**, handling **real-time updates**, and preparing **analytics-ready tables** following Lakehouse best practices.

---

## Dataset Summary

**Two schemas provided by Databricks**

### v01 – Core Retail Company

* **customers** – US customers
* **sales** – Item-level transactions
* **sales_orders** – Purchase orders
* **Streaming (retail-pipeline)**

  * customers (CDC events)
  * orders (order activity)
  * status (order lifecycle updates)

### v02 – Subsidiaries & Expansion

* Three subsidiaries with **different formats & schemas**

  * Bright Home (CSV)
  * Lumina Sports (CSV)
  * Northstar Outfitters (JSON)
* Designed to simulate **company expansion, schema normalization, and multi-source ingestion**

---

## What Was Implemented

* **Batch ingestion (v01 source files)**
  Standardized messy CSV/JSON data using explicit schemas, safe casting, date normalization, and column restructuring.

* **Streaming ingestion (v01 retail-pipeline)**
  Implemented **Auto Loader (`cloudFiles`)** to ingest incremental JSON files with schema enforcement and checkpoints.

* **Delta Lake architecture**
  Stored cleaned batch and streaming outputs as **Delta tables** under Unity Catalog.

* **UPSERT / MERGE logic**
  Integrated streaming tables with base tables using business keys to handle inserts and updates.

* **Data validation & sanity checks**
  Verified ingestion correctness using:

  * `_metadata.file_path`
  * row-count reconciliation
  * ordering and spot checks against source files

* **Standardized schemas across sources**
  Ensured consistent data models across batch, streaming, and subsidiary datasets.

---

## Key Engineering Concepts Used

* Auto Loader (schemaLocation + checkpointLocation)
* Structured Streaming
* Delta MERGE (upsert)
* Schema enforcement & evolution
* Metadata-based validation
* Unity Catalog–compatible storage

---

## Outcome

* Batch + real-time ingestion
* Clean Silver tables
* Cross-source standardization
* Scalable design for future subsidiaries (v02)

---
messy data : <img width="2940" height="1912" alt="image" src="https://github.com/user-attachments/assets/80d834d3-194b-4d58-bcc5-d1b99da53610" />

to this:(after flattening and exploding and using escape and quote options)
<img width="2940" height="1912" alt="image" src="https://github.com/user-attachments/assets/dc4e71de-01a8-4ad4-bd9b-9607dca1f8c8" />
<img width="2940" height="1912" alt="image" src="https://github.com/user-attachments/assets/9c38b1a8-19eb-4a46-afe4-c65576ce30c0" />






