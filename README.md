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

["mode","source_file","source_sheet","date","time","reported_at","year","month","month_name","day","dow_name","hour","route_or_line","dir_or_bound","loc_or_station","incident_text","incident_code","minutes_delay","minutes_gap","vehicle"]

### 3️⃣ Data Cleaning
- Converts `minutes_delay` and `minutes_gap` to numeric (`Int64`).  
- Replaces invalid/negative values with `NaN`.  
- Strips extra whitespace and harmonizes missing strings.  
- Merges and exports clean CSVs for both modes.

### 4️⃣ Text Normalization
Cleans incident descriptions into categorical groups:  
`Mechanical`, `Collision`, `Medical`, `Security/Police`, `Infrastructure/Signal`, `Weather`, `Operations/Staffing`, `Schedule/Headway`, `Diversion/Detour`.

### 5️⃣ Feature Engineering
Adds derived temporal features:
- `year`, `month_name`, `day`, `dow_name`, `hour`
- `is_weekend` flag  
- `peak_period` classification: **AM Peak (7–9)**, **PM Peak (16–18)**, **Off-Peak**

### 6️⃣ De-duplication
Removes duplicate entries using composite keys:
`["reported_at","route_or_line","loc_or_station","incident_code","vehicle"]`

### 7️⃣ Unified Dataset Creation
Merges bus and subway datasets into one **long-format table** (`ttc_all_clean_long.csv`) for use in **Tableau Public** and **Power BI** dashboards.

---

## 🧹 Key Functions & Logic

```python
def _normalize_incident_text(s):
    base = s.astype("string").str.lower().str.strip()
    if re.search("mechan|engine|door", x): return "Mechanical"
    if re.search("collision|crash|struck", x): return "Collision"
    if re.search("medical|injur|sick", x): return "Medical"
    ...
```
These utility functions allow full automation of the cleaning and enrichment process, adaptable to new data updates.

📊 **Outputs**

After cleaning and transformation, the following files are generated in data_processed/:

| Output File | Description |
|--------|--------------|
| bus_clean.csv | Cleaned, enriched TTC Bus delay data |
| subway_clean.csv | Cleaned, enriched TTC Subway delay data |
| ttc_all_clean_long.csv | Unified long-format dataset for BI visualization |

### 📈 Exploratory Insights (from quick_report)

Example summary statistics after cleaning:
```python
=== BUS CLEAN ===
Rows: 320,000
Time range: 2020-01-01 → 2025-09-30
Null % minutes_delay: 1.84%
Top incident categories:
Mechanical
Schedule/Headway
Security/Police
Medical
Infrastructure/Signal
```
These results confirm consistent schema alignment and reveal dominant delay causes.

### 📍 Visualization & Business Intelligence

This dataset powers Tableau Public and Power BI dashboards visualizing:

| Visualization | Description |
|---------------|-------------|
| 🕓 Delay Trend Over Time | Compare delays by month and day-of-week |
| 🚏 Top 10 Routes/Stations | Identify highest average delay routes |
| 🧭 Peak vs Off-Peak Analysis | Quantify delays by rush-hour periods |
| 💥 Incident Distribution | Categorize mechanical vs operational issues |
| 📊 Mode Comparison | Evaluate Bus vs Subway performance |

**Example BI View (Power BI)**

* Delay breakdown by Incident Type

* Peak-period vs weekend comparison

* Dynamic slicers for Year, Route/Line, and Mode

---

## 💡 Key Takeaways

* Unified 12 Excel files → one 600K+ record dataset

* Automated ETL pipeline ensures future scalability

* Feature-rich time variables enable peak/off-peak performance analytics

* Incident normalization supports actionable categorization

* Ready for Tableau / Power BI integration for BI dashboards


### 🚀 Tools & Technologies

| Category | Tools Used |
|----------|------------|
| Data Processing | Python, pandas, numpy |
| Notebook Environment | Jupyter |
| Visualization | Tableau Public, Power BI |
| Data Storage | CSV (cleaned outputs) |
| Version Control | Git, GitHub |


### 🧠 Skills Demonstrated

* Data Engineering and ETL

* Business Intelligence & Dashboarding

* Feature Engineering and Time-Series Analysis

* Text Normalization and Categorization

* Automation of Multi-File Schema Handling

* Visualization Storytelling (Power BI / Tableau)

---

## 🏁 Conclusion

This project demonstrates a full end-to-end **Business Intelligence workflow**, transforming fragmented municipal datasets into a structured analytics pipeline that generates operational insights.

It highlights my ability to:

* Engineer scalable data pipelines

* Extract actionable insights for performance optimization

* Communicate findings effectively through BI tools


### 🧩 Future Work

* Incorporate real-time delay APIs for live dashboards.

* Add geospatial mapping with folium for stop-level visualization.

* Explore predictive modeling for delay forecasting by route.

* Publish interactive Tableau Story summarizing yearly transit reliability.

---

## 👨‍💻 Author

**Khushnud Ahmed**

*MSc Data Science & Analytics, Toronto Metropolitan University*

💼 Business Intelligence | Data Analytics | Data Science


### 🏷️ Tags

#Python #DataCleaning #Tableau #PowerBI #BusinessIntelligence #ETL #DataAnalytics #TorontoTransit #UrbanMobility
