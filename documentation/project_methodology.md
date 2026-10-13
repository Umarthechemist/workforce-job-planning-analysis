# Project Methodology

## Project Context

This project was developed in response to a real workforce-management reporting requirement within a healthcare setting.

The aim was to analyse job-planned hours by profession across selected **Research & Improvement** and **Teaching & Training** activities.

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
- weekly and monthly workforce allocation;
- differences across Research & Improvement and Teaching & Training activity groups.

The requirement was translated into four analytical reporting areas:

- SPA Research & Improvement
- ED Research & Improvement
- DCC Teaching & Training
- SPA Teaching & Training

---

## 2. Data Preparation

The source data was initially reviewed in Excel before being loaded into Power BI.

A monthly planned-hours field was derived using:

```text
Hours Per Month = Hours Per Week × 4
```

This provided the monthly equivalent required for the management report.

---

## 3. Data Transformation

Power Query was used to prepare the activity-level data for analysis and modelling.

Key transformation steps included:

- assigning appropriate data types;
- removing fields not required for the analysis;
- combining `Category` and `Subcategory` into `CombinedCategory`;
- filtering incomplete or invalid activity records;
- creating a sequential `ActivityID`;
- preparing the transformed table for downstream dimension and fact queries.

The main category transformation followed:

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

The transformed data was organised into a dimensional model consisting of:

- `Fact_Activity`
- `Dim_Profession`
- `Dim_Category`

The dimension tables provide descriptive filtering context, while the fact table stores the activity-level records and numerical measures.

This structure supported profession-level and category-level analysis while keeping the DAX logic simple and reusable.

---

## 5. Measure Development

Reusable DAX measures were created for:

- Total Hours Per Week
- Total Hours Per Month
- SPA Research & Improvement
- ED Research & Improvement
- DCC Teaching & Training
- SPA Teaching & Training

The use of base measures reduced duplication and allowed category-specific calculations to be created using `CALCULATE`.

This design also allowed the measures to respond dynamically to profession and activity filters used throughout the report.

---

## 6. Dashboard Development

The final Power BI solution was designed as a multi-page dashboard.

Each reporting page included a combination of:

- KPI cards;
- profession-level comparisons;
- activity-level breakdowns;
- weekly and monthly measures;
- interactive filtering;
- navigation between reporting areas.

The dashboard was designed to allow users to move from high-level workforce allocation to more detailed analysis of individual activity groups.

---

## 7. Data Governance Approach

The original project contained internal organisational workforce data.

For portfolio publication:

- the original Excel workbook was excluded;
- the original operational Power BI file was not published;
- employee-level identifiers were not included;
- original organisational totals were not disclosed;
- a separate portfolio Power BI file was created;
- the original Excel data-source connection was removed;
- synthetic activity records were generated independently in Power Query;
- the existing transformation, modelling and DAX logic was preserved;
- all published dashboard screenshots were recreated using synthetic data.

This allowed the technical solution and analytical approach to be demonstrated without exposing confidential operational information.

---

## Key Learning Outcomes

This project strengthened practical experience in:

- translating stakeholder requirements into analytical outputs;
- workforce-data preparation;
- Power Query transformation;
- dimensional data modelling;
- reusable DAX measure development;
- filter context;
- Power BI dashboard design;
- data governance;
- technical documentation;
- preparing professional analytical work for a public portfolio.

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

The public repository is designed to demonstrate the analytical method, technical implementation and problem-solving approach while ensuring that no genuine organisational workforce data is disclosed.
