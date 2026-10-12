# Project Methodology

## Project Context

This project was developed in response to a real workforce-management reporting requirement within a healthcare setting.

The aim was to analyse job-planned hours by profession across selected Research & Improvement and Teaching & Training activities.

The original operational solution used internal workforce data. The public portfolio version uses synthetic data only.

---

## Analytical Process

The project followed the workflow below:

```text
Management Requirement
        ↓
Excel Preparation
        ↓
Power Query Transformation
        ↓
Dimensional Data Model
        ↓
DAX Measures
        ↓
Power BI Dashboard
        ↓
Management Reporting
```

---

## 1. Requirement Definition

The reporting requirement focused on understanding:

- how many planned hours were allocated to specific activities;
- how those hours were distributed across professions;
- weekly versus monthly workforce allocation;
- differences across Research & Improvement and Teaching & Training activity groups.

The requirement was translated into four analytical reporting areas:

- SPA Research & Improvement
- ED Research & Improvement
- DCC Teaching & Training
- SPA Teaching & Training

---

## 2. Data Preparation

The source data was initially reviewed in Excel.

A monthly-hours field was derived using:

```text
Hours Per Month = Hours Per Week × 4
```

The prepared dataset was then loaded into Power BI.

---

## 3. Data Transformation

Power Query was used to:

- assign suitable data types;
- remove unnecessary fields;
- create a combined reporting category;
- remove incomplete activity records;
- create a unique activity identifier;
- prepare the data for dimensional modelling.

The central transformation created:

```text
Category + Subcategory = CombinedCategory
```

Example:

```text
SPA + Research & Improvement
=
SPA Research & Improvement
```

---

## 4. Data Modelling

The transformed data was organised using a dimensional model with:

- `Fact_Activity`
- `Dim_Profession`
- `Dim_Category`

This structure supported profession-level and category-level analysis while keeping the DAX measures relatively simple.

---

## 5. Measure Development

Reusable DAX measures were created for:

- Total Hours Per Week
- Total Hours Per Month
- SPA Research & Improvement
- ED Research & Improvement
- DCC Teaching & Training
- SPA Teaching & Training

The use of base measures reduced duplication and allowed category-specific measures to be created using `CALCULATE`.

---

## 6. Dashboard Development

The final Power BI report was designed as a multi-page dashboard.

Each reporting page included a combination of:

- KPI cards;
- profession-level comparisons;
- activity-level breakdowns;
- weekly and monthly measures;
- interactive filtering;
- navigation between reporting areas.

The dashboard was designed to allow management users to move from high-level workforce allocation to detailed activity analysis.

---

## 7. Data Governance Approach

The original project contained internal organisational workforce data.

For portfolio publication:

- the original Excel workbook was excluded;
- the original Power BI file was not published;
- employee-level identifiers were removed;
- original organisational totals were not disclosed;
- a separate Power BI portfolio copy was created;
- the original data source connection was removed;
- synthetic activity records were generated independently in Power Query;
- all portfolio screenshots were recreated using synthetic data.

This allowed the technical solution to be demonstrated without exposing operational data.

---

## Key Learning Outcomes

This project strengthened practical experience in:

- translating stakeholder requests into analytical requirements;
- workforce-data preparation;
- Power Query transformation;
- dimensional modelling;
- DAX measure development;
- filter context;
- Power BI dashboard design;
- data governance;
- technical documentation;
- preparing professional work for a public portfolio.

---

## Portfolio Summary

This project demonstrates more than dashboard creation.

It shows an end-to-end analytical workflow:

```text
Business Problem
→ Data Preparation
→ Transformation
→ Modelling
→ Calculation
→ Visualisation
→ Governance
→ Documentation
```

The public repository is designed to demonstrate the analytical method and technical implementation while ensuring that no genuine organisational workforce data is disclosed.
