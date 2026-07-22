# Urban Mobility and Economic Productivity in LATAM Cities
---
Find out if there is a correlation between transportation structure and PIB in certain cities for the Latin American Development Bank, which wishes to identify which cities to invest in transportation infrastructure to improve productivity and population well-being.

#### Tools & Skills
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Data Cleaning](https://img.shields.io/badge/Data_Cleaning-00599C?style=for-the-badge&logo=google-sheets&logoColor=white)
![Data Transformation](https://img.shields.io/badge/Data_Transformation-E25A1C?style=for-the-badge&logo=apache-hop&logoColor=white)
![Data Analysis](https://img.shields.io/badge/Data_Analysis-295F98?style=for-the-badge&logo=analytics&logoColor=white)

### Key Business Questions
1. Which cities exhibit severe traffic congestion paired with low economic productivity?
2. Which cities demonstrate the strongest combined indicators—balancing efficient transit mobility with robust economic performance?
3. Which key variables show the strongest correlation with long-term urban and economic development?

### Data Source and Overview 
This project integrates two primary data sources to evaluate the relationship between urban traffic congestion and macro-economic performance across global metropolitan areas. 

* **TomTom Traffic Data (`tomtom_traffic.csv`):** Real-time congestion, delay times, and traffic indexes provided by TomTom's global geolocation services.
* **OECD Urban Economy Data (`oecd_city_economy.csv`):** Annual socioeconomic, productivity, and environmental indicators published by the OECD (Organization for Economic Cooperation and Development).

---

#### 1. Traffic Congestion Dataset (`tomtom_traffic.csv`)
* **Granularity:** Snapshot update per city.
* **Primary Key / Join Field:** `City` (standardized name) & `Country`.

| Field Name | Data Type | Description |
|---|---|---|
| `Country` | String | ISO-3 country code (e.g., `"ARE"` for UAE) |
| `City` | String | Standardized city or metropolitan area name |
| `UpdateTimeUTC` | DateTime | Timestamp of the traffic status measurement (UTC) |
| `JamsDelay` | Float | Total traffic delay time across monitored roads (minutes) |
| `TrafficIndexLive` | Float | Current congestion index ($0–100$; higher = more congestion) |
| `JamsLengthInKms` | Float | Total active traffic jam length (km) |
| `JamsCount` | Integer | Total count of active traffic bottlenecks |
| `TrafficIndexWeekAgo` | Float | Historical congestion index recorded 7 days prior |
| `UpdateTimeUTCWeekAgo` | DateTime | Reference timestamp from 7 days prior |
| `TravelTimeLivePer10KmsMins` | Float | Average time required to travel 10 km under live traffic (minutes) |
| `TravelTimeHistoricPer10KmsMins` | Float | Baseline historic travel time for 10 km under free-flow conditions (minutes) |
| `MinsDelay` | Float | Average delay per 10 km caused by congestion (`TravelTimeLive` - `TravelTimeHistoric`) |

---

#### 2. Economic Indicators Dataset (`oecd_city_economy.csv`)
* **Granularity:** Annual records per city.
* **Primary Key / Join Field:** `City` (standardized name) & `Year`.

| Field Name | Data Type | Description |
|---|---|---|
| `Year` | Integer | Reporting year for economic indicators |
| `City` | String | City or metropolitan area name |
| `Country` | String | Full country name |
| `City GDP/capita` | Float | Gross Domestic Product per capita (USD) |
| `Unemployment %` | Float | Unemployment rate among the economically active population (%) |
| `PM2.5 (μg/m³)` | Float | Annual average fine particulate matter concentration (Air Quality Index) |
| `Population (M)` | Float | Total metropolitan population (Millions) |

---

### Methodology
- **Data Cleaning and Validation:** Standardized column names and converted data types (including dates and numerical values) across datasets to enable seamless joins and accurate calculations, while filtering records by year to isolate the most recent and relevant data.
- **Exploratory Data Analysis & Merging:** Calculated traffic averages by city, country, and year, then merged the traffic and economic datasets into a unified, city-level dataset for integrated analysis.
- **Data Visualization:** Generated scatter plots and visual distributions using Python's Seaborn and Matplotlib libraries to explore underlying patterns and correlations between traffic metrics and economic performance.

### Insights & Key Findings 

#### 1. Economic & Mobility Decoupling
> **Macro-Level Insight:** No direct correlation was found between GDP per capita and traffic congestion. Cities with similar economic outputs exhibit vastly different traffic profiles, demonstrating that financial growth does not inherently dictate congestion levels.

#### 2. Regional Traffic Disparities & Economic Benchmarks
* **Highest Congestion Hub:** **Mexico City** registered the highest average traffic delay times across all evaluated metropolitan regions.
* **Comparative Discrepancies:** **Montevideo** achieved the highest GDP per capita while maintaining remarkably low congestion. Similarly, **Porto Alegre** and **Recife** share nearly identical traffic levels despite Porto Alegre’s higher GDP, while **Rio de Janeiro** manages far lower congestion than **Lima** at comparable GDP levels.

#### 3. Anomaly & Outlier Identification
* **Data Skewing:** Uncovered extreme outliers within the dataset that skewed macro-level trendlines, highlighting the need for isolated local variables in future urban planning models

### Strategic Recommendations

#### 1. Data Source Validation & Re-Analysis
Given the presence of extreme outliers, cross-validate raw data sources and data collection protocols before secondary analysis. Refining dataset integrity will provide clearer, unskewed visibility into potential relationships between congestion and economic productivity.

#### 2. Targeted Infrastructure Investment
* **Priority Zone:** **Santiago** presents relatively high congestion alongside the lowest economic productivity in the dataset.
* **Investment Hypothesis:** If leadership operates on the premise that mitigating traffic friction directly unlocks economic output—despite current cross-city ambiguity—Santiago represents the primary candidate for high-impact infrastructure investment.
* **Prerequisite:** Final capital allocation should remain strictly contingent on deeper diagnostic modeling following data source validation.
