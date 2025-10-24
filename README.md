# 🚗 Vehicle Telemetry Pipeline – Azure Data Engineering Project

This project implements a real-time data ingestion pipeline that validates and ingests vehicle telemetry JSON files into an Azure SQL Database using Azure-native services. It features secure storage mounting, file validation, automated triggers, and layered data transformation.

---

## 📌 Project Overview

- 🚀 **Trigger:** JSON file dropped into Azure Blob Storage (`input/`)
- 🧪 **Validation:** Azure Function verifies file structure
- 📁 **Routing:**
  - ✅ Valid files → `staging/`
  - ❌ Invalid files → `rejected/`
- 🔄 **Orchestration:** Azure Data Factory (ADF) triggers on new files
- 🧱 **Transformation:** Databricks processes data and inserts into SQL table

---

## 📐 Architecture

```plaintext
Blob Storage (input/)
     ↓
Azure Function (Blob Trigger)
     ↓
 ┌────────────┬────────────┐
 │  staging/  │ rejected/  │
 └────────────┴────────────┘
     ↓
Storage Event Trigger → ADF → Databricks Notebooks
     ↓
Azure SQL Database (VehicleData Table)
