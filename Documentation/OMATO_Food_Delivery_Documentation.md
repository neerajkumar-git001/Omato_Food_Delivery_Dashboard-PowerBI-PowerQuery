# OMATO Food Delivery Dashboard
## Project Documentation

**Document Type:** Project Technical & Business Documentation  
**Project:** OMATO Food Delivery Analytics Dashboard  
**Primary Purpose:** Business performance analysis and decision support

---

## 1. Document Purpose

This document provides detailed documentation of the OMATO Food Delivery Dashboard project.

It explains the business problem, analytical objectives, source data, data preparation approach, data model, KPI logic, DAX implementation, business interpretation, tools used, and potential improvement areas.

This document is intended to explain **how the analytical solution was built and why each component was required**. It is not intended to replace the project's README file.

---

# 2. Business Context

Food delivery operations generate continuous transactional data across orders, customers, quantities, delivery status, and payment methods.

However, transaction-level data does not directly answer management questions such as:

- Are orders being fulfilled successfully?
- How significant are cancelled orders?
- Are customers returning to place additional orders?
- What is the average number of items purchased per order?
- How important is UPI as a payment method?
- Where are operational improvements required?

The project addresses this gap by converting transaction-level data into structured operational KPIs and management-level insights.

---

# 3. Business Requirements

The analytical solution should enable management to:

### BR-01: Monitor Order Performance
Track total orders and transaction activity to understand demand.

### BR-02: Monitor Delivery Performance
Measure delivered orders and delivery success rate.

### BR-03: Monitor Cancellation
Measure cancelled orders and cancellation rate to identify potential service issues.

### BR-04: Understand Customer Activity
Measure total customers, repeat customers, and order frequency.

### BR-05: Understand Order Composition
Measure total quantity and average items per order.

### BR-06: Analyze Payment Behavior
Measure UPI orders and UPI share of total orders.

### BR-07: Support Business Improvement
Use the resulting insights to identify operational, customer, and growth opportunities.

---

# 4. Project Objectives

The project was developed to:

1. Create a structured analytical view of food delivery operations.
2. Consolidate monthly sales data for analysis.
3. Establish consistent business KPIs.
4. Measure delivery and cancellation performance.
5. Understand customer repeat-order behavior.
6. Analyze order composition.
7. Understand digital payment adoption.
8. Convert operational data into actionable business insights.

---

# 5. Data Sources

The repository contains the following source files:

```text
Data/
├── January_Sales_2023.xlsx
├── February_Sales_2023.xlsx
├── March_Sales_2023.xlsx
├── April_Sales_2023.xlsx
└── Omato_Data.xlsx
```

### Monthly Sales Files

The January through April files represent monthly sales transaction data for 2023.

### Consolidated Dataset

`Omato_Data.xlsx` provides the consolidated data used as part of the analytical workflow.

---

# 6. Data Preparation

The source data requires preparation before business analysis.

The preparation workflow includes:

1. Reviewing source structures.
2. Checking field names and data types.
3. Validating order and customer identifiers.
4. Preparing delivery status values.
5. Preparing payment method values.
6. Preparing quantity and order fields.
7. Creating a dedicated calendar table.
8. Creating reusable analytical measures.

The objective is to ensure that KPI calculations are consistent and suitable for business reporting.

---

# 7. Data Model

The project uses three primary analytical components:

### Sales Data

Contains transaction-level information used for:

- Orders
- Quantity
- Delivery status
- Payment method
- Customer activity

### Customer Details

Used to identify and analyze unique customers.

### Calendar Table

Used for date-based analysis and consistent time filtering.

The calendar table is documented separately in:

```text
DAX/Calendar_Table.md
```

---

# 8. Calendar Table

The calendar table provides the date dimension required for time-based analysis.

It contains fields such as:

- Date
- Day
- Month
- Month Name
- Year
- Year Month

The detailed DAX implementation is available in:

```text
DAX/Calendar_Table.md
```

---

# 9. KPI Framework

The dashboard uses a structured KPI framework.

## Order KPIs

- Total Order
- Transaction
- Total Quantity
- Average Items Per Order

## Delivery KPIs

- Deliver Order
- Delivered Success Rate

## Cancellation KPIs

- Cancelled Order
- Cancellation Rate

## Customer KPIs

- Total Customer
- Repeat Customer
- Orders per Customer

## Payment KPIs

- UPI Orders
- UPI Share %

The detailed DAX implementation is available in:

```text
DAX/KPI_Measure.md
```

---

# 10. DAX Logic

The project uses DAX to convert transaction-level data into reusable business measures.

### Total Orders

```DAX
Total_Order =
COUNT('Sales Data'[order_id])
```

Measures the total order volume.

### Total Quantity

```DAX
Total Quantity =
SUM('Sales Data'[quantity])
```

Measures the total number of items ordered.

### Average Items Per Order

```DAX
Average Items Per Order =
DIVIDE(
    [Total Quantity],
    [Total_Order],
    0
)
```

Measures the average number of items contained in an order.

### Delivered Orders

```DAX
Deliver Order =
CALCULATE(
    [Total_Order],
    'Sales Data'[deliver_status] = "Delivered"
)
```

Measures successfully delivered orders.

### Cancelled Orders

```DAX
Cancelled Order =
CALCULATE(
    [Total_Order],
    'Sales Data'[deliver_status] = "Cancelled"
)
```

Measures cancelled orders.

### Delivered Success Rate

```DAX
Delivered Success Rate =
DIVIDE(
    [Deliver Order],
    [Total_Order],
    0
)
```

Measures the proportion of orders successfully delivered.

### Cancellation Rate

```DAX
Cancelled Rate =
DIVIDE(
    [Cancelled Order],
    [Total_Order],
    0
)
```

Measures the proportion of orders cancelled.

### Total Customers

```DAX
Total Customer =
DISTINCTCOUNT('Customer Details'[customer_id])
```

Measures the unique customer base.

### Repeat Customers

```DAX
Repeat Customer =
COUNTROWS(
    FILTER(
        VALUES('Sales Data'[customer_id]),
        CALCULATE(
            DISTINCTCOUNT('Sales Data'[order_id])
        ) > 1
    )
)
```

Identifies customers with more than one order.

### Orders Per Customer

For an average order-frequency KPI:

```DAX
Orders per Customer =
DIVIDE(
    [Total_Order],
    [Total Customer],
    0
)
```

Measures the average number of orders per customer.

### UPI Orders

```DAX
UPI Orders =
CALCULATE(
    DISTINCTCOUNT('Sales Data'[order_id]),
    'Sales Data'[payment_method] = "UPI"
)
```

Measures orders completed through UPI.

### UPI Share

```DAX
UPI Share % =
DIVIDE(
    [UPI Orders],
    [Total_Order],
    0
)
```

Measures the contribution of UPI orders to total orders.

---

# 11. Analytical Visuals

The repository contains focused KPI visuals in:

```text
PNG's/
```

Current visual assets include:

- `AVG_Item_Per_Order.png`
- `Cancellation_Rate.png`
- `Omato_Food_Delivery_Preview.jpg`
- `Success_Rate.png`
- `Total_Order.png`
- `Total_Quantity.png`

These visuals support the analysis of order demand, order composition, cancellation performance, and delivery success.

---

# 12. Tools and Technologies

## Microsoft Power BI

### Why it was used

Power BI provides the environment for data modeling, DAX calculations, KPI analysis, and executive-level visualization.

### Problem it solves

It converts prepared transaction data into a centralized analytical view that allows management to monitor business performance efficiently.

---

## Power Query

### Why it was used

Power Query is used for data preparation and transformation before analysis.

### Problem it solves

It reduces repetitive manual data preparation when working with multiple monthly Excel files and creates a more repeatable transformation workflow.

---

## DAX

### Why it was used

DAX is used to create reusable business measures.

### Problem it solves

It enables dynamic calculations such as cancellation rate, delivery success rate, repeat customers, average items per order, and UPI share.

---

## Microsoft Excel

### Why it was used

Excel is the source format for the monthly and consolidated transaction data.

### Problem it solves

It provides structured access to the underlying operational transaction data required for analysis.

---

## GitHub

### Why it was used

GitHub is used to maintain and showcase the complete analytical project.

### Problem it solves

It provides version-controlled project storage and makes the dashboard, data documentation, DAX logic, and visual outputs accessible as a professional portfolio.

---

# 13. Skills Demonstrated

## Data Analytics

- Data Cleaning
- Data Transformation
- KPI Development
- Operational Analysis
- Customer Analysis
- Performance Analysis
- Business Insight Generation

## Business Intelligence

- Executive KPI Design
- Dashboard Development
- Business Performance Monitoring
- Decision Support
- Data Storytelling

## Technical Skills

- Power BI
- Power Query
- DAX
- Data Modeling
- Excel
- GitHub

## Business Analysis

- Business Requirement Identification
- KPI Definition
- Performance Gap Analysis
- Customer Behavior Analysis
- Operational Improvement
- Data-Driven Decision Making

---

# 14. Business Interpretation

The KPI framework is designed to move beyond reporting and support business improvement.

### High Cancellation Rate

Potentially indicates issues in fulfillment, delivery operations, customer experience, or order processing.

### Low Delivery Success Rate

May indicate operational inefficiencies that require investigation.

### Low Repeat Customer Rate

May indicate opportunities to improve customer experience, service quality, loyalty initiatives, or targeted retention strategies.

### Low Average Items Per Order

May create opportunities for bundles, cross-selling, or personalized recommendations.

### High UPI Share

Indicates strong adoption of digital payment and can inform payment experience optimization.

---

# 15. Business Improvement Framework

The dashboard can support the following improvement cycle:

```text
Operational Data
       ↓
KPI Measurement
       ↓
Performance Gap Identification
       ↓
Business Investigation
       ↓
Improvement Action
       ↓
Performance Monitoring
```

This approach helps convert analytics from a reporting activity into a continuous business improvement process.

---

# 16. Project Files

```text
PowerBI-PowerQuery/
│
├── DAX/
│   ├── Calendar_Table.md
│   ├── KPI_Measure.md
│   └── gitkeep
│
├── Data/
│   ├── January_Sales_2023.xlsx
│   ├── February_Sales_2023.xlsx
│   ├── March_Sales_2023.xlsx
│   ├── April_Sales_2023.xlsx
│   ├── Omato_Data.xlsx
│   └── gitkeep
│
├── PNG's/
│   ├── AVG_Item_Per_Order.png
│   ├── Cancellation_Rate.png
│   ├── Omato_Food_Delivery_Preview.jpg
│   ├── Success_Rate.png
│   ├── Total_Order.png
│   └── Total_Quantity.png
│
├── OMATO_FOOD_DELIVERY_DASHBOARD.pbix
├── Omato_Food_Delivery_Preview.jpg
└── README.md
```

---

# 17. Future Enhancements

The analytical solution can be extended with:

- Revenue and profitability analysis
- Delivery-time analysis
- Restaurant or partner performance
- Geographic demand analysis
- Customer lifetime value
- Customer cohort analysis
- Customer retention analysis
- Peak-hour demand analysis
- Order forecasting
- Advanced customer segmentation
- Automated performance monitoring

---

# 18. Documentation Maintenance

The documentation should be updated whenever:

- New KPIs are added.
- Existing DAX measures are modified.
- New data sources are introduced.
- The data model changes.
- New dashboard pages are created.
- Business requirements change.

This keeps the analytical project transparent, reproducible, and maintainable.
