**Supply Chain Visibility Optimization** – Milestone 3

**Project Overview**

Milestone 3 focuses on evaluating supplier performance and transportation efficiency using Power BI. The dashboards provide actionable insights into supplier reliability, quality, lead time, transportation performance, shipping modes, and delivery efficiency to support data-driven supply chain decisions.

# Objectives

- Evaluate supplier performance using a supplier scorecard.
- Rank suppliers based on multiple performance metrics.
- Analyze transportation cost and shipping efficiency.
- Compare carrier and shipping mode performance.
- Identify opportunities to improve supply chain operations.

---

# Dashboard 1: Supplier Performance

## Supplier Scorecard Calculation Methodology

Supplier performance is evaluated using a composite score based on three key performance indicators:

- **Quality Score (40%)**
  - Measures the overall quality of supplied products.
  - Higher quality scores indicate better supplier performance.

- **Reliability Percentage (40%)**
  - Represents supplier delivery reliability.
  - Suppliers with higher reliability receive better scores.

- **Lead Time (20%)**
  - Measures the average delivery time.
  - Lower lead times improve the supplier score.

### Supplier Composite Score Formula

```
Supplier Composite Score =
(Quality Score × 0.40)
+
(Reliability % × 0.40)
+
((30 − Lead Time) / 30 × 100 × 0.20)

## Supplier Ranking and Benchmarking Approach

Supplier ranking is calculated using the DAX **RANKX()** function based on the Supplier Composite Score.

Suppliers are categorized into three performance levels:

| Reliability % | Tier |
|---------------|------|
| ≥ 80% | High |
| 50% – 79% | Medium |
| < 50% | Low |

The benchmarking process compares suppliers using:

- Supplier Composite Score
- Quality Score
- Reliability Percentage
- Lead Time
- Products Supplied
- Orders Fulfilled

This enables quick identification of top-performing and underperforming suppliers.

Dashboard 2: Transportation Analytics

Transportation Cost Analysis Methodology

Transportation performance is evaluated using the following KPIs:

- Average Profit Per Order
- Total Discount Given
- Average Discount Rate
- Same Day Shipping Percentage
- Total Orders
- Late Delivery Percentage

The analysis measures profitability, shipping efficiency, and discount impact across different shipping modes.

---

Route and Carrier Performance Evaluation

Transportation performance is evaluated by comparing shipping modes:

- First Class
- Second Class
- Standard Class
- Same Day

Each shipping mode is analyzed using:

- Late Delivery Rate
- Average Profit Per Order
- Total Discount Given
- Total Orders

A Matrix Heat Map is used to evaluate late delivery percentages across different Markets and Order Regions.

Conditional formatting highlights high-risk transportation routes requiring operational improvements.


Key Insights

Supplier Performance

- High-tier suppliers consistently achieved better composite scores.
- Suppliers with shorter lead times demonstrated higher operational efficiency.
- Reliability has a significant impact on supplier ranking.
- Low-tier suppliers require continuous performance monitoring and improvement.

---

Transportation Analytics

- Standard Class shipping handled the highest number of orders.
- Same Day shipping represented a smaller percentage of total shipments.
- Late delivery rates differed significantly across shipping modes.
- Certain markets and regions experienced consistently higher late delivery percentages.

---

Business Recommendations

Supplier Management

- Increase procurement from high-performing suppliers.
- Develop corrective action plans for low-performing suppliers.
- Monitor supplier lead times regularly.
- Review supplier scorecards periodically for continuous improvement.

Transportation Management

- Optimize shipping mode selection based on delivery performance.
- Reduce unnecessary discounting to improve profitability.
- Focus on regions with higher late delivery rates.
- Improve route planning and logistics scheduling.
- Monitor transportation KPIs through interactive dashboards.

Tools & Technologies

- Power BI Desktop
- Power Query
- DAX (Data Analysis Expressions)
- Data Modeling
- GitHub

Repository Structure

```
Supply_Chain_Visibility_Optimization/
└── Milestone 3/
    ├── Milestone3_PowerBI.pbix
    ├── README.md
    └── screenshots/
        ├── Supplier_Performance.png
        └── Transportation_Analytics.png
