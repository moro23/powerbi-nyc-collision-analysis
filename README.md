# NYC Motor Vehicle Collisions | A Public Safety Analysis with Power BI

This repository contains the full Power BI project for the analysis of over 2.2 million motor vehicle collisions in New York City. This business intelligence solution was developed to support the city's "Vision Zero" initiative by transforming a massive, raw dataset into an interactive dashboard that identifies high-risk areas and critical accident patterns.

---

## Live Interactive Dashboard

The full, interactive Power BI report is published to the web and publicly available for you to explore. No software is required.

**[➡️ Click Here to View the Live Interactive Dashboard](https-your-public-power-bi-url-here)**

---

## Dashboard Showcase

Here is a preview of the main pages of the report, designed to provide insights from a high-level citywide overview down to a granular analysis of contributing factors.

### Page 1: Citywide Overview
*This page provides a high-level summary of collisions across the five boroughs, tracking key metrics like total injuries and fatalities, and analyzing long-term trends.*

![Citywide Overview Screenshot](https://github.com/moro23/powerbi-nyc-collision-analysis/blob/master/Visualizations/citywide_overview.png)

### Page 2: Geospatial & Temporal Hotspots
*This page uses a heatmap to visually identify the most dangerous intersections and street segments. It also provides a deep dive into the peak hours and days of the week when collisions are most likely to occur.*

![Hotspot Analysis Screenshot](https://github.com/moro23/powerbi-nyc-collision-analysis/blob/master/Visualizations/hotspot_analysis.png)

### Page 3: Vehicle & Contributing Factors Analysis
*This page breaks down collisions by the types of vehicles involved and the primary contributing factors cited in police reports, answering questions about which vehicles are most common in accidents.*

![Vehicle Analysis Screenshot](https://github.com/moro23/powerbi-nyc-collision-analysis/blob/master/Visualizations/vehicle_factor_analysis.png)

---

## Project Objective

In support of NYC's "Vision Zero" goal to eliminate traffic fatalities, this project aimed to analyze the NYPD's massive motor vehicle collision dataset. The objective was to develop a powerful analytical tool that allows public safety analysts and city planners to move beyond raw numbers and visually identify collision hotspots, understand temporal patterns, and analyze the dynamics of accidents to support data-driven policy decisions.

---

## Technology Stack

*   **Business Intelligence:** **Power BI** (Power Query, DAX)
*   **Data Source:** **Single CSV file (2.2M+ rows)** from NYC OpenData
*   **Version Control:** **Git, Git LFS, & GitHub**

---

## Data Pipeline & Architecture

1.  **Data Sourcing:** Connected to a single, large CSV file (over 500 MB) containing 2.2 million+ records of motor vehicle collisions from the NYC OpenData portal. **Git LFS** was configured to manage this large data file within the version control system.
2.  **Data Transformation (ETL):** Utilized **Power Query** to perform extensive data cleaning and feature engineering on the large dataset. Key transformations included:
    *   Combining `CRASH DATE` and `CRASH TIME` into a single `DateTime` field for precise temporal analysis.
    *   Creating new columns for `Hour`, `Day of Week`, and `Month` to enable trend analysis.
    *   **Unpivoting** five separate vehicle type columns (`VEHICLE TYPE CODE 1-5`) into a single, normalized `Vehicle Type` column, a critical step for accurately analyzing vehicle involvement.
3.  **Data Modeling:** Architected a **Star Schema** from the single flat file to optimize performance and usability. This involved creating clean dimension tables for `Dim_Date`, `Dim_Borough`, and `Dim_VehicleType` by referencing the main fact table and removing duplicates. This modeling approach is crucial for enabling fast and intuitive filtering on a multi-million-row dataset.
4.  **DAX Calculations:** Developed a suite of DAX measures to answer key business questions. This included core metrics like `[Total Collisions]`, `[Total Injuries]`, and `[Total Fatalities]`, as well as proportional measures like `[Pedestrian Injury %]` to provide deeper analytical context.

---

## Key Insights (Pending Final Analysis)

Here are three distinct, high-impact insights derived directly from your final report:

1.  **Geographic & Temporal Hotspots Identified:** The analysis pinpoints **Brooklyn** as the borough with the highest number of both total collisions (**144K**) and fatalities (**162**) since 2020. Temporal analysis reveals a clear and dangerous daily pattern: collisions spike dramatically during the evening commute, peaking between **4 PM and 5 PM**, with **Friday** being the most frequent day for accidents. This provides specific targets for targeted traffic enforcement and public safety campaigns.

2.  **Primary Cause of Collisions is Driver Inattention:** Despite numerous potential factors, **Driver Inattention/Distraction** is overwhelmingly the leading cause of collisions, cited in **174K** incidents. This single factor is nearly four times more common than the next leading cause ("Following Too Closely"), providing a clear and actionable focus for public awareness campaigns, such as "distracted driving" initiatives.

3.  **Sedans are Disproportionately Involved in Accidents:** While a variety of vehicles are involved in collisions, common passenger cars are the most significant contributors. **Sedans (440K)** and **Station Wagons (330K)** are involved in far more accidents than any other vehicle type, including commercial vehicles like Taxis or Box Trucks. This insight can inform vehicle-specific safety messaging and engineering considerations.

### **Additional Insights (for discussion or deeper analysis):**

*   **Data Quality Limitation:** A significant number of records have "Unspecified" for the borough, vehicle type, and contributing factor. This highlights a critical limitation in the source data and suggests an opportunity for the NYPD to improve data collection consistency to enable even deeper analysis.
*   **Collision vs. Fatality Trends:** While total collisions have shown a steady decline from 2020 to 2025, fatalities peaked in 2022 and have not declined at the same rate. This suggests that while there may be fewer accidents overall, the accidents that do occur may be becoming more severe.

---

## Future Enhancements

*   **Weather Data Integration:** Join the collision data with historical weather data from a public API to analyze the correlation between weather conditions (rain, snow, fog) and collision frequency/severity.
*   **Time Series Forecasting:** Implement a time-series model to forecast the expected number of collisions in different boroughs, providing a baseline to measure the effectiveness of new safety initiatives.
*   **Contributing Factors Deep Dive:** Create a dedicated analysis page focusing on the `CONTRIBUTING FACTOR` columns to identify the leading causes of accidents, such as driver inattention, speeding, or environmental factors.

---

## Repository Structure

```
├── .gitattributes
├── .gitignore
├── README.md
├── Data/
│   └── Motor_Vehicle_Collisions_-_Crashes.csv
├── Power BI Report/
│   └── NYC Collision Analysis.pbix
├── Scripts/
│   └── DAX/
│       └── Key_Measures.dax
└── Visualizations/
    ├── Citywide_Overview.png
    ├── Hotspot_Analysis.png
    └── Vehicle_Analysis.png
```