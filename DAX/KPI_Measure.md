# 📊 KPI & Business Performance Measures

## Description

These DAX measures form the core business metrics for the Ometo Food Delivery Analytics Dashboard. They are designed to evaluate order performance, delivery success, cancellation behavior, customer activity, purchasing patterns, and payment preferences.

The measures convert transactional food delivery data into business KPIs that can support operational improvement, customer strategy, and revenue growth decisions.

---

## 🛒 Order & Transaction KPIs

### Total Orders

```DAX
Total_Order =
COUNT('Sales Data'[order_id])
```

**Purpose:** Measures the total number of orders generated during the selected period.

### Total Transactions

```DAX
Transaction =
COUNTROWS('Sales Data')
```

**Purpose:** Measures the total number of transaction records in the sales dataset.

### Total Quantity

```DAX
Total Quantity =
SUM('Sales Data'[quantity])
```

**Purpose:** Measures the total number of items ordered.

### Average Items Per Order

```DAX
Average Items Per Order =
DIVIDE(
    [Total Quantity],
    [Total_Order],
    0
)
```

**Purpose:** Measures the average number of items included in each order.

---

## 🚚 Delivery Performance

### Delivered Orders

```DAX
Deliver Order =
CALCULATE(
    [Total_Order],
    'Sales Data'[deliver_status] = "Delivered"
)
```

**Purpose:** Measures the total number of successfully delivered orders.

### Cancelled Orders

```DAX
Cancelled Order =
CALCULATE(
    [Total_Order],
    'Sales Data'[deliver_status] = "Cancelled"
)
```

**Purpose:** Measures the number of orders cancelled before successful delivery.

### Delivered Success Rate

```DAX
Delivered Success Rate =
DIVIDE(
    [Deliver Order],
    [Total_Order],
    0
)
```

**Purpose:** Measures the percentage of total orders successfully delivered.

### Cancellation Rate

```DAX
Cancelled Rate =
DIVIDE(
    [Cancelled Order],
    [Total_Order],
    0
)
```

**Purpose:** Measures the percentage of orders cancelled, helping identify potential operational or customer experience issues.

---

## 👥 Customer Analytics

### Total Customers

```DAX
Total Customer =
DISTINCTCOUNT('Customer Details'[customer_id])
```

**Purpose:** Measures the total number of unique customers.

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

**Purpose:** Identifies customers who placed more than one order, helping evaluate customer retention and repeat purchasing behavior.

### Orders per Customer

Your current formula:

```DAX
Orders per Customer =
DISTINCTCOUNT('Sales Data'[order_id])
```

does **not** calculate orders per customer. It calculates the number of distinct orders.

For an actual Orders Per Customer KPI, use:

```DAX
Orders per Customer =
DIVIDE(
    [Total_Order],
    [Total Customer],
    0
)
```

**Purpose:** Measures the average number of orders generated per customer.

---

## 💳 Payment Analytics

### UPI Orders

```DAX
UPI Orders =
CALCULATE(
    DISTINCTCOUNT('Sales Data'[order_id]),
    'Sales Data'[payment_method] = "UPI"
)
```

**Purpose:** Measures the number of orders completed using UPI.

### UPI Share

```DAX
UPI Share % =
DIVIDE(
    [UPI Orders],
    [Total_Order],
    0
)
```

**Purpose:** Measures UPI's contribution to total orders and helps understand customer payment preferences.

---

## 💼 Business Value

These measures help management evaluate:

- Overall order volume and demand.
- Delivery success and cancellation performance.
- Customer retention and repeat purchasing behavior.
- Average purchasing activity per customer.
- Customer payment preferences.
- Operational performance and potential service issues.
- Opportunities to improve customer experience and business growth.

The KPI layer provides the analytical foundation for converting food delivery transactions into actionable business intelligence.
