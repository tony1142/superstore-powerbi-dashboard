# Power BI – Superstore Sales Dashboard

A Power BI dashboard analyzing Superstore sales data (2014–2017) using custom DAX measures, time intelligence, and interactive visuals. This project demonstrates skills in data modeling, DAX development, and business intelligence reporting.

## Project Overview
The dashboard provides insights into Superstore sales, profit, and return rates across regions, products, and customer segments. It features:
- Custom DAX measures for KPIs (e.g., Sales, Profit, % Returned Orders) and year-over-year comparisons.
- A custom date table for accurate time intelligence (e.g., `SAMEPERIODLASTYEAR`).
- Interactive visuals with cross-filtering, drill-downs, and a collapsible slicer panel.
- Optimized data model using a star schema for performance.

## Explore the Dashboard
1. Download the Power BI file from `pbix/Superstore_Analytics_Dashboard.pbix`.
2. Open it in Power BI Desktop to interact with the dashboard.
3. Use the funnel icon to access the slicer panel for filtering by date, region, or segment.
4. Click any visual to cross-filter or drill down for deeper analysis.

## Dataset
The dataset used is the **Sample Superstore Sales dataset**, sourced from the Tableau Community: [Sample - Superstore Sales (Excel).xls](https://community.tableau.com/s/question/0D54T00000CWeX8SAL/sample-superstore-sales-excelxls). It includes:
- **Orders**: Transaction-level sales data (9,994 rows).
- **Returns**: Returned orders (296 rows).

For detailed dataset structure and transformations, see [dataset_details.md](dataset_details.md).

## Documentation
- **DAX Measures**: All custom measures and date table logic are documented in [dax_measures.md](dax_measures.md).
- **Dataset Details**: Data cleaning, relationships, and design notes are in [dataset_details.md](dataset_details.md).

## Repository Structure
- **pbix/**: Power BI file (`Superstore_Analytics_Dashboard.pbix`).
- **dataset_details.md**: Dataset structure, source, and transformations.
- **dax_measures.md**: DAX measures and custom date table logic.
- **docs/**: Additional documentation.
- **images/**: Icons used for the slicer panel and the portfolio page header.

## Portfolio Page
For a business-focused overview and screenshots of the dashboard, visit my portfolio page: [Power BI Analytics Dashboard](https://tonynick.notion.site/Power-BI-Analytics-Dashboard-1c59c67da0d480cdaca4d8bc3d2db77b).

*Created by Tony Nick*
