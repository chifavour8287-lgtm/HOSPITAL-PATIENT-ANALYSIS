# HOSPITAL-PATIENTS-ANALYSIS
# 🏥 Hospital Records Data Analysis — 2021 to 2024

## 📌 Overview

This project takes hospital admission records from 2021 to 2024 and turns raw data into a story about who is being admitted, what is being treated, how long patients are staying, and what everything costs. The analysis was built in three stages: data preparation in Excel, structured querying in SQL Server (SSMS), and a fully decorated three-page dashboard in Power BI.

It is part of my data analytics portfolio, documenting what I can do with real-world data from start to finish.

---

## 🎯 Questions This Project Set Out to Answer

- Which age groups make up the majority of hospital admissions, and does age affect cost?
- What are the most common medical conditions, and how are patients being treated?
- Are certain conditions tied to longer hospital stays than others?
- What is driving the highest billing amounts — the condition, the treatment, or the length of stay?
- Has anything changed year on year, in terms of admissions, length of stay, or billing?
- Which condition and treatment combinations are the most expensive on average?

---

## 📂 About the Dataset

Patient-level hospital records covering admissions from January 2021 to July 2024.

| Column | Description |
|---|---|
| Patient ID | Unique identifier per patient |
| Name | Patient full name |
| Gender | Male or Female |
| Date of Birth | Patient birth date |
| Age at Admission | Patient age when admitted |
| Age Group | Infant / Child / Youth / Young Adult / Middle Age / Elderly / Senior |
| Medical Condition | Primary diagnosis |
| Treatments | Treatment type prescribed |
| Admit Date | Date of hospital admission |
| Discharge Date | Date of discharge |
| Length of Stay | Days between admission and discharge |
| Admit Year | Year extracted from admission date |
| Admit Month Number | Month number (1–12) |
| Admit Month Name | Month name (January–December) |
| Bill Amount | Total cost of the admission |

---

## 🧹 Data Preparation

Before any analysis, the dataset went through the following in Excel:

- Removed duplicate entries and blank rows
- Standardised date formats across admission and discharge columns
- Calculated Length of Stay from the difference between Admit and Discharge dates
- Built Age Group categories from Age at Admission
- Extracted Admit Year, Month Number, and Month Name as separate columns
- Checked all bill amounts for nulls and outliers
- Confirmed no critical fields had missing values before import into SQL Server

---

## 🛠️ Tools Used

| Tool | Role |
|---|---|
| Microsoft Excel | Data cleaning and preparation |
| SQL Server Management Studio (SSMS) | T-SQL analysis — 40 queries across 5 categories |
| Power BI Desktop | 3-page interactive dashboard |

---

## 📊 Dashboard Structure

### Page 1 — Patient Demographics

Covers who is being admitted and when. Designed to give a clear picture of the patient population and how admission volumes have moved across the four years.

**Visuals on this page:**
- KPI cards — Total Patients, Average Age, Total Revenue, Condition Count, Treatment Count
- Donut chart — Patient split by Gender
- Donut chart — Total Patients by Year
- Pie chart — Average Age by Gender
- Bar chart — Patient Count by Age Group
- Line chart — Monthly Admission Trend by Year (2021–2024)
- Slicers — Year and Month filters

---

### Page 2 — Medical Conditions & Treatments

Breaks down what patients are being treated for and which treatments are being used most often.

**Visuals on this page:**
- Horizontal bar chart — Top 10 Medical Conditions by patient count
- Treemap — Most Prescribed Treatments
- Stacked bar chart — Patient Count by Condition and Gender
- Slicers — Year and Month filters

---

### Page 3 — Length of Stay 

Examines how long patients are staying and what the financial picture looks like across conditions, age groups, and years.

**Visuals on this page:**
- Bar chart — Average Length of Stay by Medical Condition
- Line chart — Year-over-Year Average Length of Stay
- Column chart — Year-over-Year Total and Average Billing
- Scatter chart — Average Bill vs Average LOS by Condition
- Matrix table — Average Billing by Year (Top 5 Conditions)
- Slicers — Year and Month filters

---

## 🔍 SQL Analysis — 40 Queries Across 5 Categories

All queries were written in T-SQL and run in SSMS against the imported dataset.

| # | Category | What It Covers |
|---|---|---|
| 1 | Patient Demographics & Volume | Total admissions, gender split, age group counts, admission trends by year and month, oldest/youngest patients |
| 2 | Medical Conditions & Treatments | Top 10 conditions, gender breakdown per condition, most prescribed treatments, treatment variety per condition |
| 3 | Length of Stay | Overall and grouped averages, LOS distribution buckets (1–7, 8–14, 15–21, 22–30 days), year-on-year change |
| 4 | Billing & Financial | Total and average billing by condition, treatment, age group, gender, and year |
| 5 | Cross-Dimensional | Bill vs LOS together by condition, outlier identification, most expensive condition-treatment combinations |

**Techniques applied:** CTEs, `RANK() OVER (PARTITION BY)`, `CASE WHEN` bucketing, subqueries for Top N filtering, `CROSS JOIN` against aggregate baselines, `COUNT DISTINCT`, `FORMAT()`, `ROUND()`

---

## 📈 Key Findings

**Demographics:**
Admissions ran consistently across all four years with no dramatic seasonal spikes. Elderly and Senior patients formed a large share of the caseload. Gender was close to 50/50 across the dataset as a whole, though individual conditions showed noticeable skew toward one gender in some cases.

**Conditions and treatments:**
Cancer, Chronic Kidney Disease, and Alzheimer's Disease recorded the highest patient volumes. Most conditions had a clearly dominant treatment associated with them. High-intensity treatments; Surgery, Chemotherapy, and Radiation Therapy, appeared less frequently overall but showed up consistently at the top whenever billing was ranked.

**Length of stay:**
Most patients fell in the 8 to 21 day range. Conditions like the common cold and minor injuries resolved quickly, while Alzheimer's Disease and fractures produced the longest average stays. Year-on-year LOS was largely stable across 2021 to 2024, suggesting consistent clinical practice throughout the period.

**Billing:**
The same conditions leading on admission volume also led on billing ; Cancer, CKD, and Alzheimer's Disease. Patients with stays exceeding 20 days carried significantly higher bills than those discharged within 10 days. A gradual upward trend in average billing was visible year on year, likely reflecting either rising treatment costs or increasing case complexity.

**Cross-dimensional view:**
A scatter analysis of average bill against average length of stay revealed that most conditions cluster at the lower end of both axes. A small group of complex conditions sat far out from the rest , long stays and high bills simultaneously. A handful of outliers also appeared where the bill was high but the stay was short, and vice versa, which raises questions about treatment intensity versus duration.

---

## 💡 Recommendations

1. Discharge planning processes should be reviewed for conditions consistently producing long stays , particularly Alzheimer's Disease and fractures , to identify where delays might be reduced without compromising care quality
2. High-volume conditions like Cancer and CKD should be given dedicated capacity planning attention, given their combined impact on both bed days and billing
3. The upward trend in average billing warrants further investigation , whether this reflects actual cost increases, complexity shifts, or billing practice changes
4. Conditions sitting in the "long LOS / low bill" quadrant of the scatter analysis may indicate underpricing or inefficient billing practices worth reviewing
5. Age group should be factored into any resource allocation model ; Elderly and Senior patients consistently place higher demand on both bed days and costs

---

## 🚀 Skills Demonstrated

Data Cleaning · SQL Querying (T-SQL) · Window Functions · CTEs · Exploratory Data Analysis · Power BI Dashboard Design · DAX Measures · Data Visualisation · Healthcare Analytics · KPI Development · Cross-Dimensional Analysis · Data Storytelling

---

## 📸 Dashboard Preview


### Page 1 — Patient Demographics
<img width="1018" height="556" alt="PATIENTS DEMOGRAPHICS" src="https://github.com/user-attachments/assets/7afb485c-c9b9-45db-b9b9-038385ed09f9" />

### Page 2 — Medical Conditions & Treatments
<img width="1021" height="558" alt="MEDICAL CONDITIONS   TREATMENTS" src="https://github.com/user-attachments/assets/6e06032e-4ea5-4dc6-adea-990d8a1456c6" />


### Page 3 — Length of Stay & Billing
<img width="1023" height="556" alt="LENGTH OF STAY" src="https://github.com/user-attachments/assets/f52cb30b-b0c0-485c-9dae-a7213d29ce06" />



---

## 📌 Conclusion

This project shows how a healthcare dataset can move from a spreadsheet to a set of structured questions, to 40 SQL answers, to a dashboard that makes the story visible. The findings around age, condition severity, length of stay, and billing all point in consistent directions , and that consistency is what makes the insights credible. For anyone working in healthcare administration or resource planning, this kind of analysis provides a foundation for decisions that are driven by evidence rather than assumption.

---

