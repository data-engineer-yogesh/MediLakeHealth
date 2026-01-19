# 🏥 MediLake Health – EHR Delta Lakehouse Platform

An end-to-end **Healthcare Electronic Health Record (EHR) Lakehouse** built using **Databricks & Delta Lake**, designed to practice **advanced Delta pipelines, performance optimization, and exam-ready design patterns**.

This project follows a **Medallion Architecture** - (Bronze–Silver–Gold Lakehouse architecture), similar to real-world healthcare analytics platforms.

---

## 🚀 Project Objectives

- Build a production-style **EHR Data Lakehouse**
- Master **Delta Lake MERGE, SCD Type-2, and CDC patterns**
- Apply **partitioning, Z-Ordering, OPTIMIZE, and VACUUM**
- Create **analytics-ready Gold tables**
- Prepare for **Databricks Data Engineer certification & interviews**

---

## 🧱 Architecture Overview

Raw JSON (EHR Data)
↓
Bronze Layer
(Raw, Append-only)
↓
Silver Layer
(Cleaned, SCD, MERGE)
↓
Gold Layer
(Aggregated, Analytics-ready)


```
medilake-health-ehr-lakehouse/
│
├── data/
│   ├── patients.json            # Patient master data (SCD source)
│   ├── encounters.json          # Hospital visits & admissions
│   ├── diagnoses.json           # Diagnosis details per encounter
│   ├── procedures.json          # Medical procedures performed
│   ├── lab_results.json         # Lab test results (append-only)
│   └── medications.json         # Prescribed medications
│
├── notebooks/
│   ├── 01_bronze_ingestion.ipynb        # Raw JSON → Bronze Delta tables
│   ├── 02_silver_transformations.ipynb  # MERGE, SCD Type-2, data cleansing
│   ├── 03_delta_optimization.ipynb      # Partitioning, Z-ORDER, OPTIMIZE
│   └── 04_gold_analytics.ipynb          # Business metrics & aggregations
│
├── diagrams/
│   └── lakehouse_architecture.png       # Bronze–Silver–Gold architecture diagram
│
└── README.md                     # Project overview & documentation

```


---

## 🥉 Bronze Layer – Raw Ingestion

**Purpose**
- Store raw EHR data as-is
- Enable replayability and auditing

**Key Features**
- JSON ingestion using PySpark
- Schema inference
- Append-only Delta tables
- Ingestion timestamp tracking

**Bronze Tables**
- `bronze.patients`
- `bronze.encounters`
- `bronze.diagnoses`
- `bronze.procedures`
- `bronze.lab_results`
- `bronze.medications`

---

## 🥈 Silver Layer – Clean & Conform

**Purpose**
- Apply business rules
- Handle updates and late-arriving data
- Create analytics-ready dimensions & facts

**Key Implementations**
- **SCD Type-2** for patient demographics
- **MERGE INTO** for CDC handling
- Deduplication using window functions
- Active medication logic

**Silver Tables**
- `silver.patients_scd` (SCD Type-2)
- `silver.encounters_clean`
- `silver.diagnoses_clean`
- `silver.lab_results_clean`
- `silver.medications_clean`

---

## ⚡ Delta Lake Performance Optimization

**Techniques Used**
- Partitioning on date-based columns
- Z-Ordering on high-cardinality filters
- OPTIMIZE for small file compaction
- VACUUM for storage cleanup
- Partition-pruned MERGE operations

**Optimization Examples**
- Partition by `encounter_date`, `result_date`
- Z-ORDER by `patient_id`, `encounter_id`

---

## 🥇 Gold Layer – Analytics & Reporting

**Purpose**
- Provide fast, business-ready datasets
- Minimize joins for dashboards & reporting

**Gold Tables**
- `gold.patient_clinical_summary`
- `gold.hospital_utilization_metrics`
- `gold.disease_prevalence_daily`
- `gold.lab_abnormal_trends`

**Use Cases**
- Patient-level clinical summaries
- Hospital admission & LOS analysis
- Disease prevalence trends
- Lab abnormality monitoring

---

## 🧠 Key Concepts Practiced

- Delta Lake ACID transactions
- SCD Type-2 implementation
- MERGE vs INSERT vs OVERWRITE
- Partitioning vs Z-Ordering
- Bronze–Silver–Gold design principles
- Exam-style decision rules

---

## 🛠️ Technologies Used

- **Databricks**
- **Apache Spark (SQL & PySpark)**
- **Delta Lake**
- **JSON**
- **SQL Analytics**

---

## 🎯 Who This Project Is For

- Aspiring **Data Engineers**
- Databricks **certification candidates**
- Engineers preparing for **Lakehouse design interviews**
- Anyone learning **Delta Lake performance tuning**

---



---

## 📬 Future Enhancements

- Streaming ingestion using Auto Loader
- Data quality checks (expectations)
- Unity Catalog integration
- BI dashboard integration

---

## ⭐ If You Found This Useful

Give this repo a ⭐ and feel free to fork or extend it!

Happy Learning 🚀
