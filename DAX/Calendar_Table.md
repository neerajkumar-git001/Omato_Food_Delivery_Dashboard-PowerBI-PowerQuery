# 📅 Calendar Table

## Description

The Calendar Table provides a dedicated date dimension for the Ometo Food Delivery Analytics Dashboard. It enables consistent time-based analysis across daily, monthly, and yearly business performance.

The table supports trend analysis, date filtering, monthly reporting, and time-based business comparisons.

## Business Purpose

The Calendar Table helps analyze:

- Daily order and sales patterns
- Monthly business performance
- Yearly performance trends
- Seasonal demand patterns
- Time-based growth and performance changes

## DAX Implementation

### Calendar Table

```DAX
Calendar Table =
CALENDAR(
    DATE(2023, 1, 1),
    DATE(2023, 4, 30)
)
```

### Day

```DAX
Day =
FORMAT('Calendar Table'[Date], "DDDD")
```

### Month Number

```DAX
Month Number =
MONTH('Calendar Table'[Date])
```

### Month Name

```DAX
Month Name =
FORMAT('Calendar Table'[Date], "MMMM")
```

### Year

```DAX
Year =
YEAR('Calendar Table'[Date])
```

### Year Month

```DAX
Year Month =
FORMAT('Calendar Table'[Date], "YYYY-MM")
```

## Business Value

The Calendar Table provides a reliable foundation for time-based analysis, allowing business users to identify demand patterns, monitor performance trends, and make better planning decisions based on historical business activity.
