# Supply Chain Visibility Optimization – Milestone 4

## Project Overview

Milestone 4 focuses on **warehouse efficiency, supply chain KPIs, executive-level performance monitoring, and sales forecasting** using Power BI.

The dashboard provides a consolidated view of order performance, supplier reliability, warehouse utilization, inventory efficiency, dead stock, fulfillment, and sales trends. The objective is to help management identify operational bottlenecks and make data-driven supply chain decisions.

---

# Objectives

- Analyze warehouse utilization and capacity performance.
- Measure warehouse throughput and productivity.
- Develop an executive-level supply chain dashboard.
- Monitor important operational KPIs.
- Forecast future sales using historical monthly sales data.
- Optimize dashboard performance and usability.
- Identify key business risks and improvement opportunities.

---

# Warehouse Utilization Calculation Methodology

Warehouse utilization measures how efficiently the available warehouse capacity is being used.

The utilization percentage is calculated using the warehouse utilization data available in the dataset.

### Utilization KPI

```text
Warehouse Utilization % =
Used Warehouse Capacity / Total Warehouse Capacity × 100
```

The dashboard uses the **average utilization percentage** to evaluate overall warehouse efficiency.

The following utilization indicators are monitored:

- Average Utilization %
- Maximum Utilization %
- Minimum Utilization %
- Warehouse Capacity
- Remaining Capacity
- Critical Warehouses

### Capacity Risk Classification

Warehouses are classified based on utilization:

| Utilization | Risk Level |
|---|---|
| ≥ 90% | Critical |
| 75% – 89% | Watch |
| < 75% | OK |

This classification helps identify warehouses that may require capacity expansion or inventory redistribution.

---

# Throughput and Productivity KPI Calculations

Warehouse throughput measures the volume of goods processed or shipped through warehouses.

### Warehouse Units Shipped

```text
Warehouse Units Shipped =
SUM(Order Item Quantity)
```

This KPI represents the total number of units shipped from the warehouse.

### Order Count

```text
Order Count =
DISTINCTCOUNT(Order ID)
```

### Units per Order

```text
Units per Order =
Warehouse Units Shipped / Order Count
```

This metric indicates the average number of units processed per order.

### Remaining Capacity

```text
Remaining Capacity =
Average Warehouse Capacity − Total Stock
```

These KPIs are used together to evaluate warehouse productivity and identify warehouses with high workload or inefficient capacity utilization.

---

# Executive Dashboard Design Methodology

The Executive Dashboard was designed to provide senior management with a **single-page overview of supply chain performance**.

The dashboard contains KPI cards, gauges, trend analysis, slicers, tables, and narrative insights.

## KPI Cards

The executive dashboard includes:

- Total Orders
- Product Categories
- Fulfillment Rate
- Total Warehouses
- Total Suppliers
- Dead Stock Quantity

These KPIs provide a quick summary of overall supply chain performance.

## Performance Gauges

The dashboard uses gauge visuals for:

- Late Delivery %
- Average Supplier Reliability %
- Warehouse Utilization %
- Inventory Turnover Ratio

Targets are included where applicable to compare actual performance against desired performance levels.

## Interactive Filters

Slicers are provided for:

- Market
- Category
- Order Date

These filters allow users to analyze performance for specific markets, product categories, and time periods.

## Sales Trend Analysis

A line chart displays:

```text
Total Sales by Order Month
```

This allows users to identify historical sales patterns and future trends.

## Regional Analysis

A table containing:

- Order Region
- Total Sales

is used to compare regional sales performance.

## Smart Narrative

A Power BI Smart Narrative is included to summarize important trends and performance indicators automatically.

---

# Forecasting Implementation Approach

Sales forecasting is implemented using historical monthly sales data.

## Step 1: Create Order Month

A calculated column is created to group orders by month.

```DAX
Order Month =
DATE(
    YEAR(Fact_table[order_date]),
    MONTH(Fact_table[order_date]),
    1
)
```

## Step 2: Create the Sales Trend

A line chart is created using:

- **X-axis:** Order Month
- **Y-axis:** Total Sales

## Step 3: Apply Forecast

Power BI's built-in forecasting functionality is applied to the sales trend.

Forecast settings:

- Forecast length: **6 months**
- Units: **Months**
- Confidence interval/shading: **Enabled**

The forecast helps estimate future sales based on historical sales patterns.

The forecast should be interpreted as an analytical estimate rather than a guaranteed future outcome.

---

# Dashboard Optimization Techniques

Several techniques were used to improve dashboard performance and usability.

## Data Modeling

A structured data model with fact and dimension tables was used where applicable.

Dimension tables include entities such as:

- Suppliers
- Warehouses
- Shipping
- Products

This improves filtering and analytical consistency.

## DAX Optimization

Measures were created instead of unnecessary calculated columns whenever calculations needed to respond dynamically to filters.

Examples include:

- Total Orders
- Fulfillment Rate
- Late Delivery %
- Inventory Turnover Ratio
- Average Utilization %
- Total Suppliers

## Visual Optimization

The number of visuals was kept limited to the most important KPIs.

The dashboard uses:

- KPI Cards
- Gauge Charts
- Line Charts
- Tables
- Slicers
- Smart Narrative

This keeps the dashboard easy to understand and reduces unnecessary visual processing.

## Interactive Filtering

Slicers allow users to filter the dashboard by:

- Market
- Category
- Date

Cross-filtering between visuals helps users investigate performance interactively.

## Consistent Formatting

Consistent formatting was applied across the dashboard:

- Consistent font sizes
- Clear visual titles
- Consistent backgrounds
- Appropriate number formatting
- Percentage formatting for percentage KPIs
- `x` formatting for inventory turnover
- Conditional formatting where appropriate

---

# Key Insights

## Warehouse Performance

- Warehouse utilization varies across different warehouse locations.
- Warehouses approaching or exceeding 90% utilization require immediate monitoring.
- High utilization can indicate potential capacity constraints.
- Low utilization may indicate underused warehouse capacity.
- Comparing utilization with units shipped helps identify warehouse productivity differences.

## Supply Chain Performance

- Fulfillment rate provides an overview of successful order completion.
- Late delivery percentage highlights delivery performance issues.
- Supplier reliability helps identify suppliers requiring performance improvement.
- Dead stock represents inventory that may require liquidation, redistribution, or improved demand planning.
- Inventory turnover helps evaluate how efficiently inventory is converted into sales.

## Sales Performance

- Monthly sales trends provide insight into historical demand patterns.
- Regional sales comparison helps identify high- and low-performing markets.
- Six-month forecasting provides an estimate of potential future sales trends.

---

# Business Recommendations

## Warehouse Management

- Monitor warehouses approaching critical utilization levels.
- Redistribute inventory from highly utilized warehouses to facilities with available capacity.
- Consider capacity expansion when utilization remains consistently above 90%.
- Investigate underutilized warehouses to improve asset utilization.

## Inventory Management

- Identify and reduce dead stock.
- Improve demand forecasting to prevent excess inventory.
- Increase inventory turnover through better stock planning.
- Review slow-moving products regularly.

## Supplier Management

- Prioritize high-performing and reliable suppliers.
- Develop corrective action plans for low-performing suppliers.
- Monitor supplier reliability and lead time continuously.
- Use supplier scorecards for periodic performance evaluation.

## Transportation Management

- Monitor late delivery percentages by shipping mode and region.
- Improve route planning for regions with consistently high late delivery rates.
- Select shipping modes based on cost, reliability, and delivery requirements.
- Reduce unnecessary discounts where they negatively affect profitability.

## Executive Decision-Making

- Use the Executive Dashboard for regular supply chain performance reviews.
- Monitor KPI targets and investigate significant deviations.
- Use forecasting results to support inventory and capacity planning.
- Combine supplier, warehouse, transportation, and sales insights before making strategic decisions.

---

# Tools and Technologies

- **Power BI Desktop**
- **Power Query**
- **DAX (Data Analysis Expressions)**
- **Data Modeling**
- **Power BI Forecasting**
- **GitHub**

---

# Repository Structure

```text
Supply_Chain_Visibility_Optimization/
└── Milestone 4/
    ├── Milestone4_PowerBI.pbix
    ├── README.md
    └── screenshots/
        ├── Warehouse_Efficiency.png
        └── Executive_Dashboard.png
```

---

# Dashboard Screenshots

## Warehouse Efficiency

![Warehouse Efficiency](screenshots/Warehouse_Efficiency.png)

## Executive Dashboard

![Executive Dashboard](screenshots/Executive_Dashboard.png)

---

# Conclusion

The Milestone 4 Power BI solution provides an integrated view of warehouse efficiency, supply chain productivity, inventory performance, supplier reliability, transportation performance, and sales trends.

The combination of interactive KPIs, warehouse utilization analysis, forecasting, and executive-level reporting enables organizations to identify operational risks, optimize resources, and make data-driven supply chain decisions.
