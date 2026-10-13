# DAX Measures

## Overview

DAX measures were created to calculate planned workforce hours and isolate the four reporting areas required by the management request.

The solution uses reusable base measures together with category-specific measures.

---

## Base Measures

### Total Hours Per Week

```DAX
Total Hours Per Week =
SUM ( Fact_Activity[Hours per week] )
```

This measure calculates the total planned weekly hours within the current filter context.

---

### Total Hours Per Month

```DAX
Total Hours Per Month =
SUM ( Fact_Activity[Hours Per Month] )
```

This measure calculates the total planned monthly hours within the current filter context.

---

## SPA Research & Improvement

### Weekly Hours

```DAX
Hours Per Week for SPA R&I =
CALCULATE (
    [Total Hours Per Week],
    Dim_Category[CombinedCategory] = "SPA Research & Improvement"
)
```

### Monthly Hours

```DAX
Hours Per Month for SPA R&I =
CALCULATE (
    [Total Hours Per Month],
    Dim_Category[CombinedCategory] = "SPA Research & Improvement"
)
```

---

## ED Research & Improvement

### Weekly Hours

```DAX
Hours Per Week for ED R&I =
CALCULATE (
    [Total Hours Per Week],
    Dim_Category[CombinedCategory] = "ED Research & Improvement"
)
```

### Monthly Hours

```DAX
Hours Per Month for ED R&I =
CALCULATE (
    [Total Hours Per Month],
    Dim_Category[CombinedCategory] = "ED Research & Improvement"
)
```

---

## DCC Teaching & Training

### Weekly Hours

```DAX
Hours Per Week for DCC T&T =
CALCULATE (
    [Total Hours Per Week],
    Dim_Category[CombinedCategory] = "DCC Teaching & Training"
)
```

### Monthly Hours

```DAX
Hours Per Month for DCC T&T =
CALCULATE (
    [Total Hours Per Month],
    Dim_Category[CombinedCategory] = "DCC Teaching & Training"
)
```

---

## SPA Teaching & Training

### Weekly Hours

```DAX
Hours Per Week for SPA T&T =
CALCULATE (
    [Total Hours Per Week],
    Dim_Category[CombinedCategory] = "SPA Teaching & Training"
)
```

### Monthly Hours

```DAX
Hours Per Month for SPA T&T =
CALCULATE (
    [Total Hours Per Month],
    Dim_Category[CombinedCategory] = "SPA Teaching & Training"
)
```

---

## DAX Design Approach

The measure design follows a reusable calculation pattern.

The two base measures calculate total weekly and monthly planned hours. Category-specific measures then use `CALCULATE` to modify the filter context so that the same base logic can be reused for each reporting area.

The general pattern is:

```DAX
Category Measure =
CALCULATE (
    [Base Measure],
    Dim_Category[CombinedCategory] = "Required Category"
)
```

This approach reduces duplication, improves maintainability and allows the same measures to respond dynamically to profession-level and activity-level filters used throughout the report.
