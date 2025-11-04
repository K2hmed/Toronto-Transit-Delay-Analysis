# 🚌🚇 Toronto Transit Delay Analysis  
### Data-Driven Insights for Operational Efficiency

---

## 📘 Project Overview  

This project analyzes **Toronto Transit Commission (TTC)** bus and subway delay data to uncover when, where, and why transit delays occur across the city.  

Using **Python (pandas, numpy)** and **Jupyter Notebook**, the workflow merges, cleans, and standardizes 12 Excel files (6 Bus + 6 Subway) from the City of Toronto’s open data portal, creating a unified dataset that powers **interactive dashboards** in Tableau Public and Power BI.  

🎯 **Objective:**  
To identify delay patterns by route, time, and cause — enabling actionable insights for improved transit reliability and scheduling.

---

## 🧾 Data Sources  

| Source | Description | Format | Period |
|--------|--------------|---------|--------|
| City of Toronto Open Data | TTC Bus Delay Reports | Excel (.xlsx) | 2020–2025 |
| City of Toronto Open Data | TTC Subway Delay Reports | Excel (.xlsx) | 2020–2025 |

**Total Files:** 12 (6 Bus + 6 Subway)  
**Total Records:** ~600,000+  

Each file contained inconsistent column names (e.g., `route` vs `line`, `bound` vs `direction`).  
The notebook standardizes these schemas into one **clean, analyzable format**.

---

## ⚙️ Methodology  

The project implements a robust **ETL (Extract–Transform–Load)** pipeline designed for automation and reproducibility.

### 1️⃣ Data Ingestion
- Iterates through all Excel sheets in bus and subway folders.  
- Detects and unifies column variations automatically.  

### 2️⃣ Schema Standardization
Creates a consistent column structure across all datasets:

