# U.S. Flight Delay and Cancellation Analysis Dashboard

---

## Executive Summary

This project showcases my end-to-end proficiency in the **Business Intelligence (BI) workflow** using **Microsoft Power BI Desktop**. I successfully loaded, modeled, calculated, and visualized a large dataset of commercial flight records to deliver key operational insights for flight reliability analysis.

| Component | Detail | Quantified Result |
| :--- | :--- | :--- |
| **Business Problem** | Analyzing **2 million commercial flight records** for the Federal Aviation Administration (FAA) to identify critical patterns in delays and cancellations for operational improvement. | Transformed a **2 million-row** raw data source into an actionable report, enabling immediate insight generation. |
| **Solution Approach** | Developed a robust **Star Schema** data model and implemented **7 custom DAX measures** (Volume and Rate) to power a multi-faceted, interactive Flight Status Dashboard. | Metrics successfully revealed key performance indicators, such as the actual **On-Time, Delayed, and Canceled percentages** across all 2 million records. |
| **Implementation Steps** | Executed the 4-step BI Workflow: Data Loading, Relational Modeling, DAX Metric Creation, and Dashboard Visualization & Design. | Achieved a **100% data transformation completion rate** and defined a comprehensive set of reporting metrics necessary for executive review. |
| **Outcome** | Delivered a polished, scalable **Power BI Dashboard** providing real-time transparency into air traffic, carrier reliability, and primary cancellation drivers. | The resulting dashboard is optimized for stakeholder use through customized visual interactions and clean, strategic design. |

---

## Methodology: My Data Analysis Workflow

I utilized a systematic 4-step process within Power BI, ensuring data integrity and analytical rigor at every stage.

### 1. Data Loading and Preparation

* **ETL (Extract, Transform, Load):** I successfully ingested four separate CSV files, designating the largest `Flights` file as the **Fact Table** and the remaining three (`Airlines`, `Airports`, `Cancellation Codes`) as **Dimension Tables**.
* **Data Cleansing:** Using the Power Query Editor, I selected only the necessary fields and, crucially, engineered a **new calculated column** named **`Status`** using conditional logic to categorize every flight as "Canceled," "Delayed," or "On Time." This transformed a numeric data field (`Departure Delay`) into a critical categorical measure.

> **Visual: Power Query Editor - Transformation Logic**
> *This screenshot demonstrates the M-language/Power Query skills used for data cleaning and creating the critical 'Status' conditional column.*
>
> ![Power Query Editor showing data transformation steps and conditional column creation](https://raw.githubusercontent.com/ESWARMURUGAN/airline-traffic-sales-dashboard/e2827cd81774c405056915fc9ee4191b977e3561/US_flight_sales_analysis_PowerQueryEditor.png)

### 2. Relational Modeling and Star Schema

I established a best-practice **Star Schema** in the Model View, which is crucial for efficient data retrieval and accurate cross-filtering in a BI application.

* I defined **one-to-many relationships** connecting all three Dimension Tables to the central `Flights` Fact Table using appropriate foreign keys (e.g., Airline Code, Origin Airport Code). This structure allows analysis to seamlessly filter flight records based on any attribute of the airline or airport.

> **Visual: Power BI Data Model - Star Schema**
> *This visual confirms the successful creation of a robust Star Schema, a core technical requirement for BI projects.*
>
> ![Power BI Data Model showing the Star Schema connecting fact and dimension tables](https://raw.githubusercontent.com/ESWARMURUGAN/airline-traffic-sales-dashboard/e2827cd81774c405056915fc9ee4191b977e3561/US_flight_sales_analysis_DataModel.png)

### 3. DAX Metric Creation

I wrote **7 core DAX measures** to provide meaningful, aggregated metrics that go beyond simple row counts, all assigned to the `Flights` table for organizational best practices:

* **Volume Metrics:**
    * `Total Flights` = `COUNTROWS('Flights')`
    * `Canceled Flights` = `CALCULATE([Total Flights], 'Flights'[Status] = "Canceled")`
    * `Delayed Flights` = `CALCULATE([Total Flights], 'Flights'[Status] = "Delayed")`
    * `On Time Flights` = `CALCULATE([Total Flights], 'Flights'[Status] = "On Time")`

* **Rate Metrics (Key Performance Indicators):**
    * `% Canceled` = `DIVIDE([Canceled Flights], [Total Flights], 0)`
    * `% Delayed` = `DIVIDE([Delayed Flights], [Total Flights], 0)`
    * `% On Time` = `DIVIDE([On Time Flights], [Total Flights], 0)`

These formulas demonstrate proficiency in core DAX concepts, including context transition (`CALCULATE`) and error handling (`DIVIDE`).

### 4. Interactive Dashboard Design

> ![U.S. Flight Data Analysis Dashboard](https://github.com/ESWARMURUGAN/airline-traffic-sales-dashboard/blob/9f970c17098be693251a755b9922c8e4e2f11762/US_flight_sales_analysis_powerBi.png)
I designed and formatted a professional, single-page Flight Status Dashboard, prioritizing visual hierarchy and user experience.

* **Visualization:** Used **KPI Cards** for key rates, **Line Charts** for monthly trends, **Bar Charts** to compare performance across airlines and airports, and a **Donut Chart** to break down cancellation composition.
* **User Experience (UX):** I customized **Visual Interactions** to ensure selecting a filter (e.g., clicking a specific airport) correctly **refilters** (rather than highlights)
