# ✈️ OpenFlight Identifier — Mapping the Global Aviation Network

> **⚠️ Important:** Before running this project, you **must download the `110m_cultural` folder** from the [Natural Earth Data source](https://www.naturalearthdata.com/downloads/110m-cultural-vectors/) and place it in the project root directory. Without it, the world boundary maps and choropleth visualisations will fail to render.

---

## 📌 Branch Description

This subbranch (`feature/aviation-network-analysis`) contains a complete end-to-end geospatial and machine learning analysis of the global aviation network using [OpenFlights](https://openflights.org/data.html) data.

The project covers everything from raw data ingestion and quality auditing through to feature engineering, exploratory data analysis, network graph modelling, and XGBoost-based flight distance regression — all visualised with interactive maps (Folium) and publication-quality plots (Plotnine / ggplot2-style).

---

## 📁 Repository Structure

```
OpenFlight Identifier/
│
├── Mapping the Global Aviation Network.ipynb   # Main analysis notebook (100 cells)
├── Mapping the Global Aviation Network.html    # Rendered HTML export
├── Mapping-Globle-Aviation-Network-Report.pdf  # Final report PDF
├── OpenFlights_Codebook.pdf                    # Data dictionary / field reference
│
├── airports.dat        # Airport records (~7,700 airports worldwide)
├── routes.dat          # Airline route records (~67,000 routes)
├── countries.dat       # Country reference data
├── planes.dat          # Aircraft type data
│
└── 110m_cultural/      # ⚠️ NOT INCLUDED — must be downloaded separately
    ├── ne_110m_admin_0_countries.*
    ├── ne_110m_admin_1_states_provinces.*
    ├── ne_110m_populated_places.*
    └── ... (shapefiles for world boundaries)
```

---

## 🔧 Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/AjayjainNE/ML-and-Analytics-Projects.git
cd OpenFlight-Identifier
```

### 2. ⬇️ Download `110m_cultural` (Required)
Go to [https://www.naturalearthdata.com/downloads/110m-cultural-vectors/](https://www.naturalearthdata.com/downloads/110m-cultural-vectors/) and download the full cultural vector pack. Extract it so that the `110m_cultural/` folder sits at the project root alongside the `.dat` files.

> Without this folder, `geopandas` will fail to load world boundaries, and sections **6.12 (Airport Map)**, **9.4 (Great-Circle Arcs)**, and **9.5 (Choropleth)** will throw `FileNotFoundError`.

### 3. Install Python dependencies
```bash
pip install pandas numpy folium plotnine scipy scikit-learn xgboost networkx geopandas shapely
```

### 4. Launch the notebook
```bash
jupyter notebook "Mapping the Global Aviation Network.ipynb"
```

---

## 📊 Analysis Overview

| Section | Description |
|---|---|
| **1. Imports & Config** | Libraries, colour palettes, custom ggplot theme |
| **2. Data Loading** | `airports.dat` + `routes.dat` parsed into DataFrames |
| **3. Data Quality Audit** | Missingness heatmap, null counts, type checks |
| **4. Data Cleaning** | Type coercion, outlier flagging, deduplication |
| **5. Feature Engineering** | Region tags, Haversine distance, route bearing, network centrality, hub scores |
| **5.5 Interactive Map** | Folium choropleth map with layered controls |
| **6. EDA (13 plots)** | Bar, histogram, KDE, box, violin, scatter, heatmap, facet plots by region |
| **7. Normality Assessment** | QQ plots + Shapiro-Wilk tests on distance and altitude |
| **8. XGBoost Regression** | Predict flight distance; correlation heatmap, actual vs predicted, residuals, feature importance |
| **9. Network Analysis** | In-degree log–log, betweenness centrality violin, great-circle arc map, choropleth |
| **10. Bonus Visuals** | Bearing rose chart, hub-spoke diagram, cumulative coverage curve, altitude-diff scatter |

---

## 📦 Data Sources

| File | Source |
|---|---|
| `airports.dat` | [OpenFlights Airports Database](https://openflights.org/data.html) |
| `routes.dat` | [OpenFlights Routes Database](https://openflights.org/data.html) |
| `110m_cultural/` | [Natural Earth — 1:110m Cultural Vectors](https://www.naturalearthdata.com/downloads/110m-cultural-vectors/) *(download required)* |

---

## 👤 Author

**Ajay Khadke** 

---

## 📄 Licence

Data from Natural Earth is public domain. OpenFlights data is provided under the [Open Database Licence (ODbL)](https://opendatacommons.org/licenses/odbl/1-0/). Project code is for academic use.
