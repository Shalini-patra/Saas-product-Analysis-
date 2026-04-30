# PDFPulse Analytics 📊
### End-to-End SaaS Analytics Project — EditEvolv Platform

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-PostgreSQL-336791?logo=postgresql&logoColor=white)
![Looker Studio](https://img.shields.io/badge/Looker_Studio-Dashboard-4285F4?logo=google&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-Data_Source-34A853?logo=googlesheets&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

---
![Dashboard Preview](Saas_Analytics_Dashboard.pdf)

🔗 [View Full Interactive Dashboard](https://datastudio.google.com/reporting/0179066d-e14b-4a04-91ff-bece66ddc984)

---

## 📌 Project Overview

**PDFPulse Analytics** is a complete end-to-end data analytics project built for **EditEvolv**, a PDF converter and document tools SaaS platform.

The company had a rich stream of user behavior data but no structured analytics pipeline, no unified dashboard, and no framework for turning that data into business decisions.

This project delivers all three — a realistic multi-table dataset, SQL and Python-based problem statements, and a 7-page interactive Looker Studio dashboard covering traffic, engagement, revenue, ad spend, and subscriptions.

---

## 🎯 Objectives

- Build a structured analytics dataset that mirrors real GA4-style web analytics for a PDF SaaS platform
- Define and solve 9 end-to-end business problem statements using SQL and Python
- Design a 7-page interactive Looker Studio dashboard for cross-functional decision making
- Surface insights on channel efficiency, churn signals, mobile conversion gaps, and subscription LTV

---

## 📁 Repository Structure

```
pdfpulse-analytics/
│
├── generate_editevolv_demo_data.py   # Generates all 11 CSV tables (214K rows)
│
├── editevolv_demo_data/              # Generated CSV files
│   ├── A1_Users_Sessions.csv
│   ├── A2_Engagement_Pages.csv
│   ├── B1_Core_Revenue.csv
│   ├── B2_Revenue_Conversions.csv
│   ├── B3_Ad_Spend.csv
│   ├── C1_Traffic_Source.csv
│   ├── C2_Device_Detail.csv
│   ├── D1_Page_Performance.csv
│   ├── D2_Events.csv
│   ├── E1_Location.csv
│   └── subscriptions.csv
│
├── sql/                              # SQL problem statement queries
│   ├── PS1_channel_roas.sql
│   ├── PS2_bounce_anomalies.sql
│   ├── PS3_churn_signals.sql
│   ├── PS4_geo_revenue_gap.sql
│   └── PS5_device_conversion_gap.sql
│
├── python/                           # Python analysis notebooks
│   ├── PS6_traffic_forecast.ipynb
│   ├── PS7_campaign_attribution.ipynb
│   ├── PS8_user_segmentation.ipynb
│   └── PS9_subscription_ltv.ipynb
│
├── dashboard/                        # Dashboard design assets
│   ├── blueprint.png                 # 7-page layout blueprint
│   ├── color_palette.md
│   └── calculated_fields.md
│
├── reports/
│   └── PDFPulse_Analytics_Report.docx
│
└── README.md
```

---

## 🗂️ Dataset

Generated using `generate_editevolv_demo_data.py` — a Python script that simulates 6 months of realistic web analytics data (Oct 2024 – Apr 2025) with organic growth trends, weekend dips, seasonal campaign spikes, and channel-level noise.

| Table | Rows | Description |
|-------|------|-------------|
| A1_Users_Sessions | 8,688 | Daily sessions, bounce rate, engagement by device & channel |
| A2_Engagement_Pages | 8,688 | Session duration, page views, scroll depth, WAU/MAU |
| B1_Core_Revenue | 5,083 | Transactions, revenue per user, key events by campaign |
| B2_Revenue_Conversions | 3,620 | Conversion metrics, purchaser rates, lead gen events |
| B3_Ad_Spend | 3,295 | Ad cost, clicks, impressions, CPC, ROAS by campaign |
| C1_Traffic_Source | 38,006 | Sessions by source, medium, and channel |
| C2_Device_Detail | 58,558 | Sessions by device, OS, browser, and language |
| D1_Page_Performance | 8,145 | Page views, bounce, engagement, scroll by page & device |
| D2_Events | 52,128 | Event counts and key events by event name & channel |
| E1_Location | 27,150 | Users, sessions, engagement by country & city |
| subscriptions | 1,623 | Plan, price, duration, quota usage per subscription |
| **Total** | **214,984** | |

---

## 🔍 Problem Statements

### SQL-Based (PS-1 to PS-5)

| ID | Problem | Tables | Business Impact |
|----|---------|--------|-----------------|
| PS-1 | Channel efficiency — rank channels by ROAS, flag campaigns < 2 | B1, B3 | Cut wasteful ad spend |
| PS-2 | Bounce anomalies — pages with bounce > 60% & high traffic | D1, A1 | Fix broken UX |
| PS-3 | Churn signals — quota exhaustion vs conversion rate | subscriptions | Improve upsell triggers |
| PS-4 | Geo revenue gap — high-traffic, low-conversion countries | E1, B1 | Target geo campaigns |
| PS-5 | Device conversion gap — mobile vs desktop revenue difference | A1, B1, C2 | Prioritize mobile UX |

### Python-Based (PS-6 to PS-9)

| ID | Problem | Method | Business Impact |
|----|---------|--------|-----------------|
| PS-6 | Traffic forecasting — predict next 4 weeks per channel | Prophet / ARIMA | Early warning system |
| PS-7 | Campaign attribution — first-touch vs last-touch vs linear | Multi-touch attribution | Smarter budget decisions |
| PS-8 | User segmentation — cluster users by behavior | K-means (k=3) | Personalize user journeys |
| PS-9 | Subscription LTV — value by plan tier, churn-to-price ratio | LTV modeling | Optimize pricing strategy |

---

## 📊 Dashboard — Looker Studio

A 7-page interactive dashboard built in Looker Studio, connected to Google Sheets.

**Layout:** 1200 × 1000 px canvas | Left nav panel (navy `#1A3C6E`) | Top filter bar (gray `#F1F3F4`)

**Report-level filters:** Date range · Channel · Device · New vs Returning · Country

| Page | Focus |
|------|-------|
| 1. Home · Executive Pulse | KPI scorecards, session trends, channel mix |
| 2. Traffic & Acquisition | Channel volume, source treemap, bounce vs sessions |
| 3. Engagement & Behavior | Engagement heatmap, session duration, top events |
| 4. Page Performance | Page table, bounce bar chart, quality scatter quadrant |
| 5. Revenue & Conversions | Revenue trend, conversion funnel, campaign table |
| 6. Ad Spend & Campaigns | Spend vs ROAS bubble chart, campaign breakdown |
| 7. Location & Devices | World geo map, country table, device/OS/browser splits |

### Key Calculated Fields

```
Weighted Bounce Rate      = SUM(bounceRate * sessions) / SUM(sessions)
Weighted Engagement Rate  = SUM(engagementRate * sessions) / SUM(sessions)
Subscription Duration     = DATE_DIFF(end_time, start_time, DAY)
Is Active                 = CASE WHEN end_time >= TODAY() THEN 1 ELSE 0 END
```

---

## ⚙️ Setup & Usage

### 1. Generate the dataset

```bash
# Install dependencies
pip install pandas numpy

# Run the generator
python generate_editevolv_demo_data.py
```

This creates an `editevolv_demo_data/` folder with all 11 CSV files.

### 2. Load into Google Sheets

- Upload each CSV to a separate sheet tab in one Google Sheets workbook
- Rename each tab to match the table name (e.g. `a1_users_sessions`)
- Format the `date` column in each sheet: Format → Number → Date time

### 3. Connect to Looker Studio

- Go to https://lookerstudio.google.com → Create → Report
- Add data source → Google Sheets → select your workbook
- Repeat for all 11 sheets via Resource → Manage added data sources
- Verify all date columns are type **Date & Time** and numeric columns are type **Number**

### 4. Run SQL queries

The `sql/` folder contains all 5 query files. These use standard PostgreSQL syntax and can be run in any PostgreSQL-compatible environment (Cloud SQL, Supabase, local PostgreSQL, etc.)

### 5. Run Python notebooks

```bash
pip install pandas numpy scikit-learn prophet matplotlib seaborn
jupyter notebook python/
```

---

## 🛠️ Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| Python | 3.10+ | Data generation, ML analysis |
| pandas | latest | Data manipulation |
| numpy | latest | Numerical operations |
| scikit-learn | latest | K-means clustering (PS-8) |
| Prophet | latest | Time-series forecasting (PS-6) |
| SQL | PostgreSQL syntax | Analytical queries (PS-1 to PS-5) |
| Google Sheets | — | Data source layer |
| Looker Studio | — | Interactive dashboard |

---

## 📈 Key Insights Discovered

1. **Mobile conversion gap** — Mobile drives ~40% of sessions but converts at a fraction of desktop rates, representing the largest single revenue opportunity on the platform
2. **Quota exhaustion = upsell signal** — Users who exhaust their free PDF quota before plan end are the highest-intent upgrade cohort
3. **Enterprise is under-promoted** — Despite the highest retention rate among paid plans, Enterprise is the least marketed tier
4. **ROAS < 2 campaigns** — Several paid campaigns operate below break-even — the CPC vs ROAS bubble chart segments these into a clear "Cut" quadrant
5. **Pricing page scroll depth** — Users who scroll past 50% of the pricing page convert at significantly higher rates, suggesting layout optimization as a quick win

---

## 👤 Author

**[Your Name]**  
Data Analyst Intern  
[Your LinkedIn] | [Your Email]

---

## 📄 License

This project uses simulated/demo data and is intended for educational and portfolio purposes only. No real user data from EditEvolv was used.
