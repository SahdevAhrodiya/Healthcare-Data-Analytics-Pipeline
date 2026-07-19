# Healthcare Operational Data Analytics Pipeline
### Data Analysis Project (Excel → SQL → Power BI)

## 📌 Project Overview
This repository features an end-to-end data analytics enterprise pipeline built to ingest, clean, model, and visualize a health system dataset encompassing **3,500 unique patient records** and **9,000 distinct inpatient encounters**[cite: 1]. The primary goal was to resolve messy front-end intake variations, build a structured relational database architecture, and engineer an executive-facing Power BI dashboard to optimize revenue cycle operations, evaluate medical staff capacity, and mitigate clinical quality penalties[cite: 1].

## 🛠️ Tech Stack & Tools
* **Data Transformation Layer:** Microsoft Excel & Power Query
* **Relational Storage & Modeling Layer:** SQL (Structured Query Language)
* **Business Intelligence & Analytics Engine:** Microsoft Power BI & DAX

---

## 🏗️ Data Pipeline Architecture & Workflow

### **Phase 1: Ingestion & Data Cleansing (Excel & Power Query)**
* **Text & Duplicate Normalization:** Applied `TRIM`, `CLEAN`, and `PROPER` functions to standardize row entries and systematically removed 150 duplicate records using the native deduplication engine.
* **Date Engineering:** Fixed destructive, mixed date strings (`D/M/Y`, `Y/M/D`, `M/D/Y`, `D-M-Y`) and unified them into a database-compliant standard format (`Y-M-D`) using custom columns, column splitting, and text merging.
* **Imputation & Anomalies:** Handled corrupted data points by substituting blank satisfaction scores and unrealistic age rows (e.g., blanks, `-1`, `999`) with cohort-specific median averages; isolated missing insurance attributes by populating them with the distinct identifier `"N/A"` to prevent financial reporting drops.
* **Feature Engineering:** Generated new analytical metrics directly into the table, including `Waived_Amount` (Gross Charges - Net Paid), `Year_Quarter`, and patient length of stay (`Stay_Days`).

### **Phase 2: Relational Schema & Query Engine (SQL)**
* **Data Modeling:** Normalized the flat dataset into a relational **Star Schema** utilizing explicit Primary Key (PK) and Foreign Key (FK) table relationships across data boundaries (`Fact Admissions`, `Dim Patients`, `Dim Doctors`).
* **Analytical Coding & Transformations:** Deployed aggregations (`SUM`, `AVG`, `COUNT`), datasets combinations (`UNION ALL`), multi-table connectors (`LEFT/RIGHT JOIN`), and logical data branching (`CASE WHEN`) to prepare highly structured views.
* **Advanced Logic:** Utilized Window Functions (`PARTITION BY`, `RANK()`, `ORDER BY`) and complex Common Table Expressions (CTEs) to isolate provider-level productivity indexes and identify top-performing medical staff.

### **Phase 3: Visual Analytics Engine (Power BI)**
* **DAX Modeling Engine:** Transformed the database metrics into native, high-performance DAX measures to compute core clinical and financial KPIs dynamically (e.g., **Net Conversion Rate**, dynamic admissions velocity, and **30-Day Readmission Risk** metrics).
* **UI/UX Dashboard Blueprint:** Designed a high-impact, interactive multi-page dashboard targeting three critical healthcare themes:
  1. **RCM & Financial Performance:** Tracking the conversion of $147.38M in gross charges into $115.90M net allowed revenue, while auditing leakage within unallocated insurance classes.
  2. **Patient Demographics:** Exposing localized service line volume deficits—such as Cardiology pulling only 726 admissions compared to General Surgery's 1,812—despite carrying identical pricing models.
  3. **Clinical Quality & Satisfaction:** Mapping out the facility's 18.14% cross-diagnosis 30-day readmission exposure to protect the network from value-based purchasing penalties.

---

## 📊 Key Business Insights & Outcomes
* **Intake Governance Leakage:** Isolated an unallocated financial leak totaling **$1.6M in gross charges** sitting inside the missing insurance profile ("N/A"), providing a direct target for front-end registration remediation.
* **Capacity Headroom:** Proved that while Cardiology underperforms in total collections, the medical staff operates at an average census of only **4 patients per day per provider**, confirming immediate internal capacity to absorb a 300% volume increase without expanding headcount.
* **Clinical Readmission Exposure:** Identified a dangerous post-discharge care gap: readmission rates steadily decline through post-operation Day 4, but violently **spike to a 25.00% peak by Day 12**, identifying a critical need for structured transitional care coordination for high-acuity cohorts.

---

## Repository Map
* *Data Preparation:* Compare the [Raw Data Sheet](Raw_Data_Healthcare_Project.xlsx) against the finalized [Cleaned Data Sheet](Cleaned_Data_Healthcare_Project.xlsx) to review data transformation steps.
* 📜 *Database Configurations:* Review the [SQL Database Structure & Table Setup Script](SQL_Data_import_and_Setup_Healthcare_Project.txt).
* 🔍 *Analytical Code:* Inspect the [SQL Queries File](SQL_Analysis_queries_Healthcare_project.txt) containing complex aggregation, filtering, and analysis logic.
* 📊 *Interactive Dashboard:* Download and interact with the native [Power BI Dashboard Application File](Healtcare_Project_Dashboard.pbix).
* 📄 *Pipeline Documentation:* Read the comprehensive [Executive Report and Process Presentation PDF](Report_and_Pipeline_Healthcare_Project.pdf) outlining the complete lifecycle.
  
---

**Author:** Sahdev  
*Portfolio Project for Data Analytics Profiles.*
