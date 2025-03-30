# DAX Measures – Superstore Power BI Dashboard

This file contains all custom measures created in the Key Measures table for the Power BI report. These Data Analysis Expression measures support the KPI panel, YoY comparisons, and profitability insights.

---

## Core KPIs

```dax
Sales = SUM(Orders[Sales])

Profit = SUM(Orders[Profit])

% Returned Orders = 
VAR _total_orders = DISTINCTCOUNT(Orders[Order ID])
VAR _returned_orders = DISTINCTCOUNT(Returns[Order ID])
RETURN DIVIDE(_returned_orders, _total_orders)
```

---

## Prior Year (PY) Metrics

```dax
Sales PY = 
CALCULATE(
    [Sales],
    SAMEPERIODLASTYEAR('Date Table'[Date])
)

Profit PY = 
CALCULATE(
    [Profit],
    SAMEPERIODLASTYEAR('Date Table'[Date])
)

% Returned Orders PY = 
CALCULATE(
    [% Returned Orders],
    SAMEPERIODLASTYEAR('Date Table'[Date])
)
```

---

## YoY % Change Calculations

```dax
vs PY - Sales = 
DIVIDE([Sales] - [Sales PY], [Sales PY])

vs PY - Profit = 
DIVIDE([Profit] - [Profit PY], [Profit PY])

vs PY - % Returned Orders = 
[% Returned Orders] - [% Returned Orders PY]
```

---

## Custom Columns (Date Table)

These calculated columns were added to the `Date Table` to enable accurate grouping and clean labeling.

```dax
Start of Month = EOMONTH([Date], -1) + 1

Month Year Label = FORMAT('Date Table'[Start of Month], "MMM YYYY")
```

---

## Date Table Creation

A custom date table was created using DAX to enable consistent year-over-year (YoY) calculations and avoid Power BI’s automatic date hierarchy issues.

```dax
Date Table = 
ADDCOLUMNS(
    CALENDAR(MIN(Orders[Order Date]), MAX(Orders[Order Date])),
    "Start of Month", EOMONTH([Date], -1) + 1
)
```

---

## Notes

- All measures are stored in a dedicated **Key Measures** table for organization.
- `Date Table[Start of Month]` is used on time-series visuals.
- `% Returned Orders` is based on distinct count of `Order ID` matches between the Returns and Orders tables.
