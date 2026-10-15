# Green Solutions Financial & Project Analytics |  Power BI · Power Query · DAX

## Project Overview
Green Solutions is a Power BI portfolio project that explores financial performance, project budgets, and cash flow for a fictional sustainability-focused business operating across multiple countries.
This first version contains three report pages: Financial Overview — Local Currency, Project Performance, and Cash Flow & Collections. It demonstrates data preparation, semantic modeling, DAX calculations, and interactive report development using a synthetic Excel dataset.
Delivery approach: two milestones within the initial project scope. V1 implements the first deliverable: local-currency reporting. V2 is planned as a refined version of the same solution, with semantic-model improvements and both local-currency and consolidated EUR analysis to complete the intended scope.

## Business Objectives
- Compare revenue and expenses over time and across transaction categories.
- Monitor project counts, delivery status, and recorded budget figures.
- Analyze cash inflows, outflows, and invoices classified as pending or overdue.
- Provide a consistent report layout with navigation and filtering for further investigation.
- Complete the initial reporting scope in V2 with local-currency detail and consolidated EUR analysis, supported by a refined semantic model.

## Dashboard Preview
### Financial Overview — Local Currency
<img width="1153" height="646" alt="Financial Overview" src="https://github.com/user-attachments/assets/ca186b6d-505c-4f37-8d27-f7d1410178f9" />

Revenue, expenses, revenue less expenses, and overdue revenue, supported by monthly trends, category comparisons, and a financial detail table.

### Project Performance
<img width="1128" height="647" alt="Project Perfomance" src="https://github.com/user-attachments/assets/7baf17f2-c0a6-4696-b3f6-9d8b07c53a4c" />

Project counts by status, estimated versus actual budget fields, and project-level details including expected and actual ROI values.

### Cash Flow & Collections
<img width="1129" height="639" alt="Cash Flow" src="https://github.com/user-attachments/assets/257628a6-78f2-4b01-b710-834374762cab" />

Monthly inflows and outflows, geographic comparisons, invoice-status composition, and customer-level pending and overdue amounts.


## Key Insights
The following observations describe the filters shown in the previews, rather than company-wide conclusions:
- Mexico, 2025: the Financial Overview displays approximately 157.34 million in revenue and 168.54 million in expenses, producing a difference of approximately −11.19 million in local currency (MXN).
- Under the same Overview filters, approximately 50.30 million MXN is classified as overdue revenue. This uses the source invoice-status label; it is not a calculation of days past due.
- In the Project Performance preview, with Mexico selected and all years displayed, the model returns 491 projects: 120 active, 135 completed, 102 delayed, and 134 in planning. These reflect the current model's geographic filter path and are not necessarily projects located in Mexico.
Cash-flow totals across different local currencies are not interpreted as consolidated financial results.

## Data Overview
Source: a supplied synthetic Excel workbook, green_solution_financial_dataset(1).xlsx. The data is used for demonstration and does not represent an actual company's results.
|Table|	Records|	Main information|
|--|--|--|
|dim_date|	1,826	|Daily calendar from January 2022 to December 2026|
|dim_region	|8	|Country, city, continent, and currency|
|dim_customer|	1,000|	Customer attributes, industry, and contract dates|
|dim_project|	4,000	|Project attributes, status, budgets, and ROI fields|
|fact_transactions|50,000|	Revenue and expense transactions, categories, and invoice status|
|fact_cashflow|	5,000	|Cash inflows, outflows, and net movements|
|fact_operational_costs|	12,000	|Project-related operational costs|
|fact_esg_metrics|	15,000|	Environmental measurements and ESG scores|

Amounts are treated as local currency. The dataset includes EUR, USD, MXN, BRL, CLP, and COP. ESG and operational-cost tables are available in the source but do not have dedicated report pages in this V1.

## End-to-End Workflow

### Data Understanding
Reviewed the workbook structure, table roles, identifiers, date coverage, monetary fields, and available business categories. Identified interpretation questions involving local currencies, project assignments, budgets, and ROI.

### Data Ingestion
Imported the Excel tables into Power BI Desktop using Power Query.

### Data Preparation
Used Power Query to prepare the imported tables for the model, including column-type configuration. Kept separate business processes in their own tables rather than merging all facts into one dataset.
Further reconciliation of synthetic-data assignments is part of the improvement backlog.

### Data Modeling
Built a model with multiple fact tables and shared dimensions. V1 combines direct dimension-to-fact relationships with dimension chains involving region, customer, and project, giving it a hybrid constellation/snowflake structure.
Active and inactive relationships determine filter propagation. A future version will simplify these paths into a clearer constellation of stars after the underlying business rules are resolved.

### Measures and Calculations
Used DAX measures for:
- Revenue and expenses filtered by transaction type.
- Revenue less expenses.
- Pending and overdue revenue filtered by invoice status.
- Cash inflows, outflows, and net cash flow.
- Distinct project counts and project counts by status.
- Estimated and actual budget aggregation.
- Display of expected and actual project ROI fields.
Revenue less expenses is distinct from net cash flow and is not labeled as accounting net profit.

### Dashboard Development
Developed three pages with a consistent ceramic-inspired blue palette, KPI cards, line and bar charts, detail tables, slicers, and sidebar navigation.
Financial Overview supports year, month, and country filtering. Project Performance adds project-status filtering. Cash Flow & Collections includes year, month, and continent filters.

## Technology Stack

| Technology | Application |
|---|---|
Power BI | Desktop	Semantic model, interactive reports, and navigation
Power Query / M |	Excel ingestion and data preparation
DAX	| Measures, filtered calculations, and aggregations
Excel|	Synthetic source dataset

## Project Value
The report provides a structured way to explore financial movements, project status, and invoice classifications from a multi-table dataset. It brings summary indicators and supporting detail into a consistent interface.
As a portfolio project, it demonstrates the development of a Power BI reporting solution while making its data assumptions and current limitations explicit. Delivery in two milestones also makes the evolution of the requirements implementation, model, and report reviewable, with validation evidence to be documented between versions.
### V2 — Planned Scope
V2 will be developed in a separate branch. It will adjust and refine V1 in accordance with the initial project scope, providing two complementary views:
|Reporting view	|Purpose|
|--|--|
Local Currency	|Preserve country-level financial detail in the original currency, with single-currency filtering.
Consolidated EUR	|Convert supported monetary indicators to EUR so countries can be compared and combined on a common currency basis.

The planned work includes:
- Refine the semantic model into a clearer constellation of stars and simplify filter paths.
- Reconcile customer, project, region, and date assignments before relying on cross-table comparisons.
- Prepare monthly exchange-rate keys and implement EUR measures with explicit conversion-date rules for each monetary indicator.
- Document the selected monthly-closing-rate methodology as a management-reporting assumption, rather than claiming statutory accounting consolidation.
- Validate rate coverage and prevent missing or future exchange rates from producing partial totals.
- Align visual labels, units, filters, and financial definitions across the local and consolidated views.
- Define budget semantics and portfolio-level ROI methodology.
- Verify visual field bindings and reconcile totals before and after the model changes.
The second milestone is intended to complete the original local and consolidated reporting scope, rather than introduce an unrelated project.
These capabilities remain planned and are not presented as completed V1 features. Completion will depend on documented validation against the agreed reporting definitions.

---

## Author

**JRAMOSP**

BI & Data Engineering Professional | Microsoft Certified

[GitHub](https://github.com/jmramosp)
