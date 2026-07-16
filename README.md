# Global Seismic Analytics: Microsoft Fabric Lakehouse Platform

An end-to-end data engineering and business intelligence platform built entirely within **Microsoft Fabric**, migrating legacy-style reporting into a scalable **Medallion Lakehouse architecture**[cite: 3, 4].

---

## 📌 Project Overview
This project showcases the modernization of an analytics platform by building an automated, production-grade data pipeline in Microsoft Fabric[cite: 3, 4]. 

By orchestrating automated pipelines, the system ingests semi-structured seismic activity data from the United States Geological Survey (USGS) API, processes it through structured Bronze and Silver refinement layers, and models a business-ready Gold curated layer[cite: 4]. The final output delivers high-performance semantic models powering dynamic executive Power BI dashboards[cite: 3, 4].

---

## 🏗️ Architecture & Data Flow

### 1. Ingestion (Bronze Layer)
* **Tooling:** Fabric Data Factory Pipelines
* **Implementation:** Established scheduled REST API calls to pull real-time nested JSON payloads from the USGS server. Data is stored directly as raw Delta tables within OneLake to preserve historical states.

### 2. Transformation & Cleansing (Silver Layer)
* **Tooling:** Fabric Notebooks (PySpark / SQL)
* **Implementation:** Flattened complex nested JSON arrays, applied schema enforcement, handled null/anomalous values (e.g., coordinate out-of-bounds checks), and converted timestamps to standard business zones.

### 3. Dimensional Modeling (Gold Curated Layer)
* **Tooling:** Lakehouse SQL Analytics Endpoint
* **Implementation:** Transformed clean Silver tables into an optimized Star Schema consisting of:
  * `Fact_Seismic_Events`: Magnitude, depth, significance metrics.
  * `Dim_Geography`: Regional coordinates, place names.
  * `Dim_Time`: Calendar details for time-intelligence capabilities.

### 4. Semantic Modeling & BI
* **Tooling:** Power BI & Direct Lake Mode
* **Implementation:** Built robust, scalable semantic models bypassing import/DirectQuery storage modes for maximum performance. Authored standardized DAX measures to calculate Year-over-Year (YoY) metrics and custom risk performance KPIs.

---

##  Tech Stack & Skills Highlighted
* **Cloud Platform:** Microsoft Fabric (OneLake, Lakehouse, Data Factory, Notebooks)
* **Languages:** PySpark, Spark SQL, T-SQL, DAX
* **Storage Engine:** Delta Lake / Parquet
* **Visualization:** Power BI Desktop & Service

---

##  Key Enhancements Implemented
* **Medallion Pipeline Partitioning:** Partitioned the Silver delta tables to optimize query performance when pulling historical monthly data.
* **Direct Lake Optimization:** Configured semantic models utilizing Direct Lake mode to ensure near-real-time executive dashboard updates without manual dataset refreshes.
* **Standardized Governance:** Implemented mock security roles (RLS) and standardized KPI definitions in the semantic layer to align with modern corporate data governance standards.

---

## 📖 Learning Context
*This project was developed as a hands-on deep dive into Microsoft Fabric's Medallion architecture, building upon baseline USGS data pipeline concepts. I implemented the baseline architecture and extended it by engineering the custom Star Schema, building the Semantic Model, and configuring advanced Direct Lake performance optimizations to replicate real-world enterprise analytics environments.*
