# 🌍 Galamsey Impact Tracker

**A relational database and analytics project tracking the water and public health impact of illegal mining (galamsey) in Ghana, 2020–2026.**

Built as the Phase 2 capstone of my self-directed AI/ML learning journey, focused on SQL, relational database design, and data visualization.

---

## 📌 Overview

Galamsey (illegal small-scale gold mining) has been steadily poisoning Ghana's rivers for years, but the scale of it is hard to grasp from headlines alone. This project turns that problem into a structured, queryable dataset: a 6-table relational database in SQLite, joined and analyzed with SQL, and visualized with Plotly, covering water quality, mining activity, water supply risk, and public health outcomes across all 16 regions of Ghana.

The goal was simple: take a real, urgent national issue and show what it looks like when you actually structure the data around it, instead of just reading about it.

---

## 🎯 Project Objectives

- Design and build a normalized relational database from scratch using SQL
- Populate 6 linked tables with research-backed real-world data for all 16 Ghana regions
- Use SQL joins, aggregations, subqueries, and connectivity analysis to extract insights
- Visualize environmental degradation, water contamination, and health impacts over time
- Identify which clean rivers are next in line for downstream contamination
- Quantify the human cost — deaths, disease cases, children affected, population at risk

---


## 🗄️ Database Schema

The database (`galamsey_tracker.db`) contains 6 relational tables:

| Table | Description |
|---|---|
| `regions` | All 16 regions of Ghana: population, area, and galamsey hotspot status |
| `rivers` | Rivers per region: length, contamination status, and downstream flow target |
| `water_quality_readings` | 126 readings (2020–2026): pH, mercury, turbidity, cyanide, and lead levels per river |
| `mining_activity` | Mining activity per region per year: hectares destroyed, number of sites, chemicals used |
| `water_supply_sources` | Water supply sources per region: contamination status, communities served, population at risk |
| `health_impact` | Health outcomes per region per year: disease type, cases, deaths, children affected |

All tables are linked with foreign keys back to `regions`, and `water_quality_readings` links to `rivers`, enabling multi-table joins across contamination, mining activity, supply risk, and health outcomes.

---

## 🧪 Data & Methodology

- Ghana Statistical Service — 2021 Population and Housing Census
- Water Resources Commission of Ghana — River Basin Reports
- Ghana Water Company Limited (GWCL) — Water Quality Bulletins
- ISSA Africa — Galamsey Environmental Impact Report, 2025
- Al Jazeera — Ghana Illegal Gold Mining Surge, January 2025
- National Commission for Civic Education (NCCE) Ghana — Health Impact Report, 2024
- World Health Organization (WHO) — Drinking Water Quality Guidelines
- WaterAid Ghana — Pra River Turbidity Documentation

> **Note on 2025–2026 data:** Values for 2025 and 2026 are projected forward
> based on confirmed 2020–2024 trends and the documented surge in galamsey
> activity following the 2024 gold price spike. They are clearly labelled
> the values in this database are **constructed, not pulled live from an official government or NGO API.** 

---

## 📊 Visualizations (18 Total)

### Water Quality Trends
- Mercury levels over time across all hotspot rivers vs WHO safe limit (0.001 µg/L)
- Pra River turbidity 2020–2026 vs GWCL treatment threshold (2,000 NTU)
- River pH distribution by region showing dangerous acidification in mining zones

### Mining Activity
- Hectares of land destroyed per region per year (2020–2026)
- Growth of active mining sites across all hotspot regions

### Health Impact
- Total health cases per region. All 16 regions including zero-case regions for comparison
- Disease breakdown per region (2024) : Chronic Kidney Disease, Respiratory Disease,
  Mercury Poisoning, Birth Defects, Neurological Disorders, Waterborne Disease
- Children affected per region over time (2020–2026)
- Deaths per region over time (2020–2026)

### Contamination Risk and Overview
- Pie chart : Ghana regions: galamsey hotspots vs unaffected (8 of 16 regions affected)
- Pie chart : Ghana rivers: contaminated vs clean
- Stacked bar : Contaminated vs clean rivers per region
- Downstream contamination risk : Which clean rivers are at risk from upstream flow
- Population at risk from contaminated water sources per region

### Correlation and 3D Analysis
- Correlation heatmap : Mercury, turbidity, pH, mining sites, hectares, health cases,
  deaths, children affected
- 3D scatter : Mercury levels vs health cases vs year, sized by total deaths

---

## 🔑 Key Findings

### 1. Pra River is Ghana's most polluted river
Mercury concentration averaged **0.0174 µg/L — 17x above the WHO safe limit**.
Turbidity reached **18,900 NTU by 2026**, nearly 10x the maximum Ghana Water Company
treatment plants can process. In August 2024, GWCL was forced to shut down water
supply to Cape Coast and surrounding communities entirely because the Pra River
was too polluted to treat.

### 2. 7,615,000 Ghanaians are drinking from contaminated water sources
Across 8 hotspot regions, over 7.6 million people are currently served by water
intakes drawing from contaminated rivers. Greater Accra alone, served by the
Weija Dam on the Densu River has **2.1 million people at risk**.

### 3. Ashanti Region leads in total deaths
Between 2020 and 2026, Ashanti recorded the highest galamsey-linked deaths,
driven by Chronic Kidney Disease and Mercury Poisoning from the Offin, Oda,
and Owabi rivers, all of which are contaminated and flow directly into the Pra.

### 4. 4,411 children have been affected
Children in hotspot regions face birth defects linked to cyanide exposure,
neurological damage from mercury vapour inhalation, and waterborne disease
from contaminated drinking sources. Every year from 2020 to 2026, the number
of children affected increased without exception.

### 5. Land destruction is accelerating, driven by gold prices
Total hectares destroyed by galamsey increased every single year. The 2024
gold price surge to $3,000 per gram triggered a massive expansion of mining
sites. Ashanti alone went from 45 sites in 2020 to 162 by 2026. Across all
hotspot regions, active sites grew from approximately 200 in 2020 to over
700 by 2026.

### 6. Downstream contamination risk is immediate
The SQL river connectivity analysis shows that the Offin, Oda, and Owabi rivers
(all contaminated, Ashanti) flow directly into the Pra River (Western Region —
already contaminated). The Birim River (Eastern Region) also flows into the Pra.
The Bisi River (Ahafo) flows into the Tano (Western Region). As upstream
contamination worsens, rivers further downstream face increasing risk even
without direct mining nearby.

### 7. Mercury and health cases have a strong positive correlation
Correlation coefficient: **0.643**, confirming that as mercury levels in rivers
rise, reported health cases in the same region rise significantly. This is not
coincidence. It is cause and effect, measurable in the data.

### 8. Bono East is an emerging hotspot. Intervention is urgent
Previously unaffected, Bono East recorded galamsey activity from 2022, with
mining sites growing from 6 (2020) to 36 (2026) and health cases appearing
for the first time. It is following the exact trajectory Ashanti was on a
decade ago. Without intervention, it is next.

---
## 🛠️ Tech Stack

- **Python 3**
- **SQLite** — relational database engine
- **SQL** — schema design, joins, aggregations
- **pandas** — data wrangling and analysis
- **Plotly Express** — interactive visualizations
- **Matplotlib / Seaborn** — supplementary static visualizations
- **Jupyter Notebook** — analysis environment

---

## ⚙️ Setup & Installation

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/galamsey-impact-tracker.git
cd galamsey-impact-tracker

# 2. Create a virtual environment (recommended)
python3 -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch the notebook
jupyter notebook Galamsey_Impact_Tracker.ipynb
```

Run all cells from top to bottom. The notebook builds the SQLite database from scratch on each run, so no external database file is required beforehand.

---

## 📁 Repository Structure

```
galamsey-impact-tracker/
│
├── Galamsey_Impact_Tracker.ipynb    # Main analysis notebook
├── galamsey.db              # SQLite database (generated on run)
├── requirements.txt                 # Python dependencies
└── README.md                        # This file
```

---

## 🚧 Limitations & Future Work

- Data is modeled/constructed rather than sourced from a single live official dataset (see **Data & Methodology** above).
- Future versions could integrate real, verifiable time-series data from Ghana Water Company or EPA Ghana, where publicly available.
- Planned next step: combine this tracking approach with a predictive machine learning model (Phase 3 of my AI/ML roadmap) to forecast contamination trends by region.
- Potential extension: a public-facing dashboard (Streamlit or Dash) so non-technical stakeholders can explore the data interactively.

---

## 👩🏾‍💻 About The Author

This project is the **Phase 2 SQL capstone** of my AI/ML roadmap, combining
relational database design, exploratory data analysis, and real-world storytelling
around a crisis that is affecting millions of Ghanaians. 

I'm Benedicta Bondzie (The Tech Diva), documenting my transition from Junior to Intermediate AI/ML Engineer in 2026, one real project at a time.

## 🌍 Connect With Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/benedicta-bondzie-the-tech-diva/)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://whatsapp.com/channel/0029VbBL8H8Elagyfxqfxg2I)
[![TikTok](https://img.shields.io/badge/TikTok-000000?style=for-the-badge&logo=tiktok&logoColor=white)](https://www.tiktok.com/@techdiva01)
[![X](https://img.shields.io/badge/X-1DA1F2?style=for-the-badge&logo=x&logoColor=white)](https://x.com/DivaInTech)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/techdiva01)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@techdivachronicles)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/qr/R4E5YUQKTWDFG1)
[![Substack](https://img.shields.io/badge/Substack-FF6719?style=for-the-badge&logo=substack&logoColor=white)](https://substack.com/@thetechdiva)
[![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/benedictabondzie)


---

## 📄 License

This project is open for educational and portfolio reference. If you build on it, a credit back to this repository is appreciated.
