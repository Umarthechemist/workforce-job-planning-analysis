# Power Query Transformations

## Overview

Power Query was used to prepare the workforce activity data for analysis and modelling in Power BI.

The transformation process converted the source activity data into a structure suitable for dimensional modelling and DAX calculations.

---

## Transformation Steps

### 1. Data Type Assignment

Appropriate data types were assigned to the source columns to ensure that text, numerical and time fields were handled correctly.

Examples included:

- text fields for profession, category and activity;
- numerical fields for planned hours;
- time fields where relevant.

---

### 2. Removal of Unnecessary Fields

The `Preferred Name` field was removed because it was not required for the management analysis.

The analysis focused on workforce activity at profession level rather than identifying individual employees.

---

### 3. Combined Category Creation

A new field called `CombinedCategory` was created by joining the `Category` and `Subcategory` fields.

The Power Query logic was:

```powerquery
[Category] & " " & [Subcategory]
```

For example:

```text
Category: SPA
Subcategory: Research & Improvement

Result:
SPA Research & Improvement
```

The resulting reporting categories included:

- SPA Research & Improvement
- ED Research & Improvement
- DCC Teaching & Training
- SPA Teaching & Training

This field was later used in DAX calculations and report filtering.

---

### 4. Filtering Invalid Records

Records were excluded where:

- `CombinedCategory` was null;
- `Activity` was null;
- `Activity` contained the value `blank`.

This ensured that only valid activity records were included in the analytical model.

---

### 5. Activity ID Creation

An index column was added starting from `1`.

The index was then renamed:

```text
Index → ActivityID
```

This created a sequential identifier for the activity-level records used in the model.

---

### 6. Column Reordering

Columns were reordered to create a clearer structure before the data was referenced by the dimension and fact queries.

---

## Downstream Queries

The transformed activity table was used as the source for:

```text
Dim_Profession
Dim_Category
Fact_Activity
```

This allowed the Power Query preparation layer to feed the dimensional model without repeating the original transformation logic.

---

## Public Portfolio Version

The original project used internal operational data.

For this public portfolio version, the original Excel source was removed and replaced with a fully synthetic Power Query dataset.

The synthetic source preserves:

- the required field structure;
- profession-level analysis;
- activity categories;
- weekly and monthly hours;
- the transformation workflow;
- the dimensional model;
- the DAX calculations.

No original workforce records or genuine organisational values are included in the public Power BI file.
