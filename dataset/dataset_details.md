# Dataset Details – Superstore Power BI Dashboard

This Power BI project is built using the publicly available Sample Superstore dataset, commonly used for training and interviews in data analytics and business intelligence. The dataset includes four years of retail transaction data, spanning orders, returns, and customer segmentation.

The primary goal of the data preparation process was to build a lean, efficient, and purpose-driven model to support key business questions around sales performance, profitability, and return rates.

---

## Tables Used

### 1. Orders

This table contains the core transaction-level sales data used to calculate sales, profit, and related KPIs.

Columns used:
- Order Date
- Order ID
- Sales
- Profit
- Category
- Sub-Category
- Region
- State
- Segment

Columns removed:
- Row ID
- Ship Date
- Ship Mode
- Product ID

These fields were not required to support the business questions being addressed and were excluded to reduce model size and improve performance.

---

### 2. Returns

This table was used to identify returned orders based on `Order ID`. It contains a simple structure with one relevant column:
- Order ID

A relationship was established between `Returns[Order ID]` and `Orders[Order ID]` to enable the calculation of return percentages.

---

## Custom Date Table

To support accurate time intelligence functions such as `SAMEPERIODLASTYEAR`, a custom date table was created using DAX. This approach avoids reliance on Power BI’s auto-generated date hierarchies, which can create multiple redundant date tables in the background and degrade performance.

### DAX Formula:

```dax
Date Table = 
ADDCOLUMNS(
    CALENDAR(MIN(Orders[Order Date]), MAX(Orders[Order Date])),
    "Start of Month", EOMONTH([Date], -1) + 1
)
```

The table was marked as a **Date Table** in Power BI and linked to `Orders[Order Date]`. `Start of Month` is used for monthly grouping in time-series visuals.

---

## Custom Columns

To improve the clarity of tooltips and categorical date displays, a clean Month-Year label was created:

```dax
Month Year Label = FORMAT('Date Table'[Start of Month], "MMM YYYY")
```

This field is used in custom tooltip pages to show readable hover labels (e.g., "Jan 2017") instead of full date stamps.

---

## Data Cleaning & Transformation Notes

- Tables were imported from `Sample - Superstore.xls`
- Headers were promoted on import
- Only necessary columns were retained
- No transformations beyond column removal and renaming were performed
- Relationships created:
  - `Orders[Order ID]` → `Returns[Order ID]`
  - `Orders[Order Date]` → `Date Table[Date]`

---

## Model & Visualization Design Notes

- A collapsible slicer panel was created using image icons, bookmarks, and selection panes to allow users to show/hide filter options intuitively.
- A tooltip page was designed for time-series visuals using a clean Month-Year label (`MMM YYYY`) to clearly display point-in-time comparisons.
- Conditional formatting was applied to profit-based visuals (map and bar chart) to highlight negative profit using red tones, improving the communication of loss-making areas.

---

## Summary

This dataset was intentionally minimized and cleaned to support a focused set of KPIs and visualizations tied directly to business performance. All enhancements were made with clarity, speed, and practical decision-making in mind.
