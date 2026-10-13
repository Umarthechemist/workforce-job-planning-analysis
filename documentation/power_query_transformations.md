# Power Query Transformations

## Overview

Power Query was used to prepare the workforce activity data for analysis and modelling in Power BI.

The transformation process converted the activity-level source data into a structured dataset suitable for dimensional modelling, DAX calculations and dashboard reporting.

---

## Transformation Steps

### 1. Data Type Assignment

Appropriate data types were assigned to the source columns to ensure that text, numerical and time-based fields were handled correctly.

Examples included:

- text fields for profession, category, subcategory and activity;
- numerical fields for planned hours;
- time fields where relevant.

---

### 2. Removal of Unnecessary Fields

The `Preferred Name` field was removed because it was not required for the analytical requirement.

The report focused on workforce activity at profession level rather than individual employee identification.

---

### 3. Combined Category Creation

A new field called `CombinedCategory` was created by concatenating the `Category` and `Subcategory` fields.

The Power Query logic was:

```powerquery
[Category] & " " & [Subcategory]
```

For example:

```text
Category: SPA
Subcategory: Research & Improvement

CombinedCategory:
SPA Research & Improvement
```

The resulting reporting groups included:

- SPA Research & Improvement
- ED Research & Improvement
- DCC Teaching & Training
- SPA Teaching & Training

The `CombinedCategory` field was later used in DAX calculations and dashboard filtering.

---

### 4. Filtering Invalid Records

Rows were filtered to exclude records where:

- `CombinedCategory` was null;
- `Activity` was null;
- `Activity` contained the literal value `blank`.

The filtering logic ensured that incomplete activity records were excluded from the analytical model.

---

### 5. Activity ID Creation

A sequential index column was added starting from `1`.

The index was then renamed:

```text
Index → ActivityID
```

This created a unique sequential identifier for each activity-level record used in the model.

---

### 6. Column Reordering

Columns were reordered to create a clearer and more consistent structure before the transformed table was referenced by downstream model queries.

---

## Downstream Queries

The transformed `TblActivityReport` query was used as the source for:

```text
Dim_Profession
Dim_Category
Fact_Activity
```

This approach allowed the main transformation logic to be defined once and then reused by the dimension and fact queries.

The resulting workflow was:

```text
Synthetic / Source Activity Data
            ↓
     TblActivityReport
            ↓
   ┌────────┼────────┐
   ↓        ↓        ↓
Dim_Profession
Dim_Category
Fact_Activity
```

---

## Public Portfolio Version

The original operational solution used an Excel workbook containing internal workforce data.

For the public portfolio version:

- the original Excel connection was removed;
- a separate synthetic Power Query source was created;
- the synthetic source feeds the existing transformation workflow;
- the dimensional model and DAX logic were preserved;
- all published dashboard values are generated from synthetic records.

The synthetic data preserves the analytical structure required to demonstrate:

- profession-level analysis;
- activity categories;
- weekly and monthly hours;
- Power Query transformations;
- dimensional modelling;
- DAX calculations;
- Power BI dashboard design.

No original workforce records, employee identifiers or genuine organisational values are included in the public Power BI file.
