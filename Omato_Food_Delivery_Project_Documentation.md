# OMATO Food Delivery Dashboard

## 1. Project Overview

The **OMATO Food Delivery Dashboard** is a business-focused analytics project designed to transform food delivery transaction data into actionable insights for operational improvement, customer understanding, and business growth.

The analysis focuses on order volume, quantity demand, delivery success, cancellation behavior, repeat customers, items per order, and payment preferences. The dashboard brings these metrics together to help management understand current performance and identify areas requiring improvement.

---

## 2. Business Problem

Food delivery businesses generate large volumes of order and customer data. Without structured analysis, it can be difficult for management to quickly identify operational issues, customer behavior patterns, and opportunities for improvement.

Key business questions addressed by this project include:

- How many orders are being generated?
- How many items are being sold?
- What percentage of orders are successfully delivered?
- What is the cancellation rate?
- How many customers return and place multiple orders?
- How many items are purchased per order?
- What is the contribution of UPI orders?
- Where should management focus operational improvements?

---

## 3. Business Objectives

The project aims to:

- Monitor overall order and transaction performance.
- Measure delivery success and cancellation performance.
- Understand customer purchasing and repeat-order behavior.
- Analyze average items per order.
- Evaluate payment preferences.
- Identify operational performance gaps.
- Support customer experience improvements.
- Provide data-driven insights for business growth.

---

## 4. Key Business KPIs

The dashboard analyzes the following core metrics:

| KPI | Business Purpose |
|---|---|
| Total Order | Measures overall order demand |
| Total Quantity | Measures total items sold |
| Average Items Per Order | Measures average order size |
| Delivered Order | Measures successfully completed orders |
| Delivered Success Rate | Evaluates delivery performance |
| Cancelled Order | Measures unsuccessful orders |
| Cancellation Rate | Identifies order loss and operational issues |
| Total Customer | Measures unique customer base |
| Repeat Customer | Measures repeat purchasing behavior |
| Orders per Customer | Measures average order frequency |
| UPI Orders | Measures UPI-based order volume |
| UPI Share % | Measures UPI contribution to total orders |
| Transaction | Measures total transaction records |

---

## 5. Data Sources

The repository contains monthly sales data for 2023 along with a consolidated dataset.

### Monthly Sales Files

- `January_Sales_2023.xlsx`
- `February_Sales_2023.xlsx`
- `March_Sales_2023.xlsx`
- `April_Sales_2023.xlsx`

### Consolidated Data

- `Omato_Data.xlsx`

These files provide the underlying transaction data used for the dashboard analysis.

---

## 6. Analytical Areas

### Order Performance

Order volume and transaction activity are analyzed to understand overall customer demand and business activity.

### Delivery Performance

Delivered and cancelled orders are evaluated to measure operational reliability and identify potential service issues.

### Customer Behavior

Customer-level analysis is used to identify repeat customers and understand purchasing frequency.

### Order Composition

Average Items Per Order helps management understand customer purchasing patterns and identify opportunities for bundles and cross-selling.

### Payment Behavior

UPI order volume and UPI share provide insight into customer payment preferences and digital payment adoption.

---

## 7. Business Improvement Opportunities

### Reduce Order Cancellations

Monitoring cancellation rate can help identify potential issues in fulfillment, delivery operations, or customer experience.

### Improve Customer Retention

Repeat-customer analysis can support targeted retention strategies and help identify loyal customer groups.

### Increase Order Value

Average Items Per Order can be used to identify opportunities for product combinations, bundles, and cross-selling.

### Improve Delivery Performance

Delivered Success Rate provides a clear measure of service reliability and can help management prioritize operational improvements.

### Strengthen Digital Payment Adoption

UPI Share analysis can help understand customer payment preferences and improve the digital checkout experience.

---

## 8. DAX Measures

The project maintains dedicated DAX documentation in the `DAX/` folder.

### Calendar Table

`Calendar_Table.md` documents the date dimension used for time-based analysis.

### KPI Measures

`KPI_Measure.md` contains the core DAX measures used to calculate order, customer, delivery, cancellation, quantity, and payment KPIs.

The DAX layer supports consistent and reusable business calculations across the dashboard.

---

## 9. Dashboard Visualizations

The `PNG's/` folder contains visual outputs used to present key business metrics.

Current visual files include:

- `AVG_Item_Per_Order.png`
- `Cancellation_Rate.png`
- `Omato_Food_Delivery_Preview.jpg`
- `Success_Rate.png`
- `Total_Order.png`
- `Total_Quantity.png`

These visuals provide focused views of important operational KPIs.

---

## 10. Power BI Dashboard

The main Power BI project file is:

`OMATO_FOOD_DELIVERY_DASHBOARD.pbix`

A dashboard preview is also available as:

`Omato_Food_Delivery_Preview.jpg`

The PBIX file contains the analytical model, calculations, and dashboard used for the project.

---

## 11. Repository Structure

```text
PowerBI-PowerQuery/
│
├── DAX/
│   ├── Calendar_Table.md
│   ├── KPI_Measure.md
│   └── gitkeep
│
├── Data/
│   ├── April_Sales_2023.xlsx
│   ├── February_Sales_2023.xlsx
│   ├── January_Sales_2023.xlsx
│   ├── March_Sales_2023.xlsx
│   ├── Omato_Data.xlsx
│   └── gitkeep
│
├── PNG's/
│   ├── AVG_Item_Per_Order.png
│   ├── Cancellation_Rate.png
│   ├── Success_Rate.png
│   ├── Total_Order.png
│   └── Total_Quantity.png
│
├── OMATO_FOOD_DELIVERY_DASHBOARD.pbix
├── Omato_Food_Delivery_Preview.jpg
└── README.md
```

---

## 12. Project Outcome

The project converts raw food delivery transaction data into structured business intelligence that can help management monitor operational performance and customer activity.

The analysis provides a foundation for identifying cancellation issues, improving delivery performance, strengthening customer retention, understanding purchasing behavior, and supporting data-driven business growth.

---

## 13. Future Business Improvements

Future analysis can extend the project with:

- Revenue and profit analysis.
- Restaurant or partner performance.
- Delivery-time analysis.
- Geographic demand analysis.
- Customer lifetime value.
- Customer retention and cohort analysis.
- Peak-hour demand analysis.
- Forecasting of future order volume.
- Customer segmentation.
- More detailed operational efficiency metrics.

---

## 14. Project Focus

The primary focus of this project is **business improvement through data**.

Rather than using analytics only to report historical performance, the dashboard is designed to help management identify operational gaps, understand customer behavior, prioritize improvement opportunities, and make better decisions that support sustainable growth.
