# Event-Driven Azure Data Factory Orchestration Pipeline

## 📌 Overview
This project demonstrates a **fully automated, event-driven Azure Data Factory (ADF) pipeline** designed using modular child pipelines and a parent orchestration pipeline.

The solution reacts to file-arrival events, orchestrates sequential pipeline execution, integrates external data via HTTP APIs, applies conditional logic and looping patterns, performs transformations using Data Flows, and delivers analytics-ready datasets into a structured Data Lake.

---

## 🚀 Key Capabilities Covered

- Event-based triggering using **Storage Event Triggers**
- Parent–child pipeline orchestration
- Sequential pipeline execution
- Dynamic file handling & cleanup
- External data ingestion via **HTTP API (GitHub)**
- Conditional processing using **If Condition + ForEach**
- Schema-based transformations using **ADF Data Flows**
- Dataset splitting, filtering, and aggregation
- Analytics-ready outputs for downstream teams

---

## 🏗️ Data Lake Folder Structure
- **Source**  
  Incoming files dropped with a specific naming convention.

- **Destination**  
  Central processing area where source files and external API data are combined and transformed.

- **Reporting**  
  Final curated datasets ready for consumption by the analytics team.

---

## 🔄 Pipeline Architecture

### **1️⃣ Storage Event Trigger**
- Monitors the **Source** folder
- Fires the **Parent Pipeline** when a file with a defined naming pattern is detected
- Enables fully automated, event-driven execution

---

### **2️⃣ Parent Pipeline**
- Acts as the orchestration layer
- Triggers multiple child pipelines **in sequence**
- Ensures controlled execution flow and dependency management

---

### **3️⃣ Child Pipeline 1 — Source File Ingestion**
- Copies the incoming file from **Source → Destination**
- Deletes the file from Source after successful copy  
  *(Prevents duplicate triggering and reprocessing)*

---

### **4️⃣ Child Pipeline 2 — External API Ingestion**
- Fetches additional data from a **GitHub repository using HTTP API**
- Stores fetched data into the **Destination** folder
- Demonstrates API-based ingestion in ADF

---

### **5️⃣ Child Pipeline 3 — Conditional Processing & Transformation**

#### **File Validation Logic**
- Uses **ForEach Activity** to iterate over files
- Uses **If Condition Activity** to:
  - Check whether required files exist
  - Ensure only **specific files** are processed (not all files)

#### **Data Transformation (ADF Data Flow)**
- Selects only required columns
- Applies transformation logic
- Splits the dataset based on conditions applied to a key column
- Produces **three separate outputs**:
  - Two condition-based datasets
  - One aggregated dataset saved directly for analytics consumption

---

## ⚙️ Tech Stack
- **Azure Data Factory**
- **ADF Pipelines & Data Flows**
- **Azure Data Lake Storage**
- **HTTP API (GitHub Integration)**
- **Event Triggers**
- **ForEach & If Condition Activities**

---

## 📊 Output for Analytics Team
- Clean, filtered, and split datasets
- One pre-aggregated table ready for reporting
- Files stored in the **Reporting** folder
- No manual preprocessing required

---

## 📈 Why This Project Matters
- Demonstrates real-world ADF orchestration patterns
- Shows understanding of event-driven pipelines
- Handles idempotency and duplicate-trigger prevention
- Combines internal and external data sources
- Delivers analytics-ready outputs, not raw dumps

---

## 🔧 Execution Flow Summary

1. File arrives in **Source** folder  
2. Storage Event Trigger fires Parent Pipeline  
3. Parent Pipeline triggers:
   - Source ingestion pipeline
   - GitHub API ingestion pipeline
   - Conditional transformation pipeline  
4. Transformed and split datasets saved into **Reporting** folder  

---

## 📬 Contact
For discussion or collaboration, reach out via LinkedIn or GitHub.
