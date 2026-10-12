# Workforce Job Planning Analysis | Power BI

## Project Overview

This project demonstrates an end-to-end workforce job-planning analysis developed in response to a real management reporting requirement within a healthcare workforce setting.

The objective was to analyse planned workforce activity across selected Research & Improvement and Teaching & Training categories, with a particular focus on:

- planned hours by profession;
- weekly and monthly workforce allocation;
- comparison of activity across professional groups;
- detailed breakdown of specific job-planning activities.

The solution was developed using **Excel, Power Query, dimensional data modelling, DAX and Power BI**.

The original operational report supported a one-off management request. This public portfolio version recreates the analytical solution using fully synthetic data.

---

## Data Governance and Confidentiality

The original project was developed using internal organisational workforce data.

To protect confidentiality and comply with information-governance requirements:

- no original employee-level data is included in this repository;
- no genuine job-plan identifiers are included;
- no original organisational totals are published;
- no original Excel source file is included;
- the public Power BI report uses completely synthetic data;
- synthetic values were generated independently rather than by scaling or masking the original figures;
- screenshots included in this repository are taken only from the synthetic portfolio version.

The synthetic dataset preserves the **structure, analytical logic and reporting requirements** of the original project while ensuring that the published figures do not represent actual organisational activity.

---

## Business Requirement

The management requirement was to produce a one-off workforce report showing planned hours **by profession**, reported both **per week** and **per month**, for four key areas.

---

## Solution Workflow

The analysis followed a structured workflow from initial data preparation through to interactive reporting.

### 1. Excel Data Preparation

The source workforce data was initially reviewed and prepared in Excel before being loaded into Power BI.

The main derived field created at this stage was:

**Monthly Planned Hours**

```text
Hours Per Month = Hours Per Week × 4

### 1. SPA Research & Improvement

Analysis was required for:

- Abstracts, publications and conference presentations
- Research activity (internally funded)
- Service development, innovation, evaluation, audit and project work

### 2. ED Research & Improvement

Analysis was required for:

- Commercial research activity
- Funded research activity and associated travel
- Principal Investigator activity

### 3. DCC Teaching & Training

Analysis was required for:

- Direct clinical training with patients
- Patient-facing clinical supervision with staff, apprentices and students

### 4. SPA Teaching & Training

Analysis was required for:

- Preceptorship activities – preceptee
- Preceptorship activities – preceptor
- Providing 1:1 peer/clinical supervision
- Receiving 1:1 peer/clinical supervision
- Teaching – attending/receiving
- Teaching – planning and delivery

---

## DAX Measures

DAX measures were created to calculate total planned workforce hours and isolate the four reporting categories required for the analysis.

### Base Measures

```DAX
Total Hours Per Week =
SUM ( Fact_Activity[Hours per week] )
```

```DAX
Total Hours Per Month =
SUM ( Fact_Activity[Hours Per Month] )
```

These measures provide the overall weekly and monthly planned hours and are reused within the category-specific calculations.

### SPA Research & Improvement

```DAX
Hours Per Week for SPA R&I =
CALCULATE (
    [Total Hours Per Week],
    Dim_Category[CombinedCategory] = "SPA Research & Improvement"
)
```

```DAX
Hours Per Month for SPA R&I =
CALCULATE (
    [Total Hours Per Month],
    Dim_Category[CombinedCategory] = "SPA Research & Improvement"
)
```

### ED Research & Improvement

```DAX
Hours Per Week for ED R&I =
CALCULATE (
    [Total Hours Per Week],
    Dim_Category[CombinedCategory] = "ED Research & Improvement"
)
```

```DAX
Hours Per Month for ED R&I =
CALCULATE (
    [Total Hours Per Month],
    Dim_Category[CombinedCategory] = "ED Research & Improvement"
)
```

### DCC Teaching & Training

```DAX
Hours Per Week for DCC T&T =
CALCULATE (
    [Total Hours Per Week],
    Dim_Category[CombinedCategory] = "DCC Teaching & Training"
)
```

```DAX
Hours Per Month for DCC T&T =
CALCULATE (
    [Total Hours Per Month],
    Dim_Category[CombinedCategory] = "DCC Teaching & Training"
)
```

### SPA Teaching & Training

```DAX
Hours Per Week for SPA T&T =
CALCULATE (
    [Total Hours Per Week],
    Dim_Category[CombinedCategory] = "SPA Teaching & Training"
)
```

```DAX
Hours Per Month for SPA T&T =
CALCULATE (
    [Total Hours Per Month],
    Dim_Category[CombinedCategory] = "SPA Teaching & Training"
)
```

The category-specific measures use `CALCULATE` to modify the filter context of the base measures. This allows the same underlying weekly and monthly calculations to be reused across each reporting area.

---

## Power BI Dashboard

The final report was designed as a multi-page Power BI dashboard to answer the management reporting requirement across the four target workforce activity areas.

### SPA Research & Improvement

![SPA Research & Improvement](images/spa-research-improvement.png)

This page summarises planned weekly and monthly hours for SPA Research & Improvement activities by profession and activity type.

### SPA Teaching & Training

![SPA Teaching & Training](images/spa-teaching-training.png)

This page shows planned workforce allocation for SPA Teaching & Training activities, including supervision, preceptorship and teaching activity.

### ED Research & Improvement

![ED Research & Improvement](images/ed-research-improvement.png)

This page analyses planned hours associated with ED Research & Improvement activities, including funded research and investigator activity.

### DCC Teaching & Training

![DCC Teaching & Training](images/dcc-teaching-training.png)

This page focuses on DCC Teaching & Training activity, including direct clinical training and patient-facing clinical supervision.

---

## Dashboard Features

The Power BI solution includes:

- weekly and monthly planned-hours KPIs;
- profession-level comparisons;
- activity-level breakdowns;
- category-specific analysis;
- interactive filtering;
- navigation between reporting pages;
- consistent visual design across all four reporting areas.

The public portfolio screenshots shown above use synthetic data only.

---

## Tools Used

This project used the following tools and technologies:

- **Microsoft Excel** – initial data review and calculation of monthly planned hours
- **Power Query** – data cleaning, transformation and preparation
- **Power BI** – data modelling, DAX calculations and dashboard development
- **DAX** – calculation of weekly and monthly workforce metrics
- **GitHub** – documentation and presentation of the portfolio project

---

## Key Skills Demonstrated

This project demonstrates practical experience in:

- translating a management request into analytical requirements;
- preparing and transforming workforce data;
- creating calculated fields and business rules;
- using Power Query for repeatable data transformation;
- building a dimensional data model;
- creating fact and dimension tables;
- defining relationships between tables;
- writing reusable DAX measures;
- applying filter context using `CALCULATE`;
- analysing workforce activity by profession;
- designing multi-page Power BI reports;
- presenting both summary KPIs and detailed activity analysis;
- documenting analytical work for a technical portfolio;
- applying data-governance principles when publishing organisational work.

---

## Repository Structure

```text
workforce-job-planning-analysis/
│
├── README.md
│
├── powerbi/
│   └── Workforce_Job_Planning_Portfolio.pbix
│
├── images/
│   ├── spa-research-improvement.png
│   ├── spa-teaching-training.png
│   ├── ed-research-improvement.png
│   └── dcc-teaching-training.png
│
└── documentation/
```

The Power BI file included in this repository contains synthetic data only.

---

## Portfolio Note

This project is based on a real workforce reporting requirement completed in a professional healthcare setting.

The public version has been recreated specifically for portfolio use. The analytical approach, transformation logic, dimensional modelling, DAX methodology and dashboard design reflect the original solution, while all published data values are synthetic.

This approach allows the technical work to be demonstrated without exposing confidential organisational or employee information.
