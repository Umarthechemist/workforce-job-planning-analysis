# Data Model

## Overview

The Power BI solution uses a dimensional model to separate descriptive attributes from activity-level measures.

The core model consists of:

```text
Dim_Profession
      |
      | 1
      |
      | *
Fact_Activity
      *
      |
      | 1
      |
Dim_Category
```

This structure supports analysis of planned workforce activity by profession, reporting category and activity type.

---

## Fact Table

### Fact_Activity

The `Fact_Activity` table contains the activity-level records used in the analysis.

Key fields include:

- `ActivityID`
- `Activity`
- `Hours per week`
- `Hours Per Month`
- `ProfessionID`
- `CategoryID`

The fact table provides the numerical activity measures used by the Power BI report.

---

## Profession Dimension

### Dim_Profession

The `Dim_Profession` table contains the professional groups associated with the activity records.

It is used to analyse planned workforce hours by profession.

Examples of profession groups in the synthetic portfolio version include:

- Physiotherapist
- Occupational Therapist
- Dietitian
- Diagnostic Radiographer
- Therapeutic Radiographer
- Speech & Language Therapist
- Orthoptist
- Rehabilitation Engineer
- Podiatrist
- Support to AHP

All profession records in the public portfolio version are synthetic.

---

## Category Dimension

### Dim_Category

The `Dim_Category` table contains the reporting categories used throughout the analysis.

The main reporting groups are:

- SPA Research & Improvement
- ED Research & Improvement
- DCC Teaching & Training
- SPA Teaching & Training

These reporting groups are created by combining the `Category` and `Subcategory` fields.

Example:

```text
Category: SPA
Subcategory: Research & Improvement

CombinedCategory:
SPA Research & Improvement
```

---

## Relationships

The model uses one-to-many relationships between the dimension tables and the fact table.

```text
Dim_Profession[ProfessionID] (1)
        |
        *
Fact_Activity[ProfessionID]

Dim_Category[CategoryID] (1)
        |
        *
Fact_Activity[CategoryID]
```

The dimension tables provide the filtering context, while `Fact_Activity` stores the detailed activity records and numerical measures.

Filtering flows from the dimension tables into the fact table, allowing profession and category selections to affect the DAX measures used throughout the report.
---

## Why a Dimensional Model Was Used

Using separate fact and dimension tables provides several benefits:

- clearer model structure;
- reduced duplication of descriptive attributes;
- easier filtering and grouping;
- simpler DAX calculations;
- improved maintainability;
- easier extension if additional reporting categories are introduced later.

The dimensional model also makes the analytical workflow easier to understand, document and maintain as part of a technical portfolio.
