# LexEuropa Legal Analytics

An end-to-end Power BI analytics project designed to monitor firm performance, evaluate lawyer productivity and workload, assess client value, and surface the drivers of profitability across a pan-European law firm's case portfolio.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Project Description](#project-description)
3. [Business Problem](#business-problem)
4. [Project Objectives](#project-objectives)
5. [Business Questions](#business-questions)
6. [About the Dataset](#about-the-dataset)
7. [Dataset Structure](#dataset-structure)
8. [Data Preparation and Transformation](#data-preparation-and-transformation)
   - [Importing the Dataset into Power BI](#importing-the-dataset-into-power-bi)
   - [Data Cleaning](#data-cleaning)
   - [Data Modelling](#data-modelling)
9. [Data Analysis in Power BI](#data-analysis-in-power-bi)
   - [DAX Measures](#dax-measures-created)
10. [Dashboard Development](#dashboard-development)
    - [Dashboard](#dashboard)
    - [Overview](#overview)
    - [Performance](#performance)
    - [Clients](#clients)
12. [Insights from the Data Analysis](#insights-from-the-data-analysis)
13. [Business Recommendations](#business-recommendations)
14. [Conclusion](#conclusion)
15. [Tools and Technologies](#tools-and-technologies)


---

## Introduction

Law firms generate large volumes of case-level data across practice areas, lawyers, clients, and offices. As caseloads grow, manually tracking profitability, lawyer capacity, case outcomes, and client value becomes increasingly difficult for partners and management to do by hand.

Business Intelligence tools such as Power BI allow firms to turn raw case data into insights that support both partner-level strategic decisions and day-to-day operational ones.

This project presents an interactive Firm Performance Analytics Dashboard developed for LexEuropa Legal Group. The dashboard gives partners and management a centralized view of revenue and profitability, case outcomes, lawyer workload, client value, and client satisfaction across the firm's 15 European offices.

Using Power BI, DAX, and a star schema data model, the solution turns case-level data into insights that can help partners improve resource allocation, protect profitability, and understand what actually drives successful case outcomes.

## Project Description

The objective of this project was to design an interactive Power BI dashboard capable of giving partners and management a decision-ready view of the firm's case portfolio.

The dashboard focuses on three major business areas:

- Firm-Wide Performance Monitoring
- Lawyer Productivity and Workload
- Client Value and Satisfaction

The solution allows stakeholders to monitor revenue, profit, case outcomes, lawyer utilization, client concentration, and satisfaction from a single reporting platform.

The dashboard was built on a dimensional data model consisting of one fact table and five dimension tables, allowing efficient filtering, aggregation, and drill-down across case, lawyer, client, office, and date dimensions.

## Business Problem

Law firms depend on case data to understand profitability, allocate lawyer capacity, and protect client relationships. Without an effective reporting solution, several challenges arise:

- Partners cannot easily monitor profitability across practice areas and offices.
- Lawyer workload imbalances go unnoticed until burnout or attrition risk becomes visible.
- Case outcomes are not consistently tied back to profitability or client satisfaction.
- High-value and strategic clients are not easily distinguished from the broader client base.
- Outstanding balances and billing performance are difficult to track at scale.
- Decision-makers lack a centralized view of firm-wide performance indicators.

These challenges can result in uneven resource allocation, lawyer overload, margin erosion, and missed opportunities to protect and grow the firm's most valuable client relationships.

To address these issues, this project delivers an interactive Power BI dashboard that enables partners to monitor key performance indicators, identify resourcing bottlenecks, and support data-driven decisions across the firm.

## Project Objectives

The primary objectives of this project were to:

- Develop an interactive Power BI dashboard for monitoring firm-wide legal performance.
- Analyze revenue and profitability across practice areas and offices.
- Evaluate lawyer workload and utilization by seniority.
- Track case outcomes and win rate.
- Identify the firm's most valuable clients and practice areas.
- Assess the relationship between client satisfaction and case performance.
- Provide partners with actionable insights for resourcing and profitability decisions.
- Support evidence-based decision-making through interactive, drill-down visualizations.

## Business Questions

The dashboard was designed to answer several key business questions, grouped by the brief's core themes:

**Revenue and Profit**
- Which practice areas and offices generate the highest revenue and profit?

**Case Outcomes**
- How do case outcomes vary across departments and lawyers?

**Lawyer Workload**
- Which lawyers have the highest utilization and workload?

**Risk and Complexity**
- How do risk, case complexity, and duration impact profitability?

**Client Value**
- Which clients and practice areas contribute the most value?

**Client Satisfaction**
- How does client satisfaction relate to case performance?

The answers to these questions enable partners to improve resource allocation, protect and grow the firm's most valuable relationships, and strengthen case outcomes going forward.

## About the Dataset

The dataset used in this project represents case-level data generated by LexEuropa Legal Group, simulating real-world law firm operations across offices, practice areas, and client relationships.

The dataset follows a dimensional modelling approach consisting of one fact table and five dimension tables. This structure enables efficient reporting, simplifies DAX calculations, and improves dashboard performance.

The analysis focuses on understanding revenue and profitability, case outcomes, lawyer workload, client value, and client satisfaction.

The dataset contains 15,000 case records involving 200 lawyers, 800 clients, and 15 offices across Europe, spanning 1 January 2024 to 31 December 2026, across 10 practice areas and 26 case types.

## Dataset Structure

The project consists of six related tables.

| Table | Description |
|---|---|
| **Fact_Cases** | Stores every legal case and serves as the central fact table for analysis. |
| **Dim_Case** | Contains case attributes: status, outcome, complexity, practice area, and priority. |
| **Dim_Lawyer** | Contains lawyer demographic and seniority information. |
| **Dim_Client** | Contains client demographic, industry, and segmentation details. |
| **Dim_Office** | Contains office location and geographic details. |
| **Dim_Date** | A standard calendar table supporting time intelligence. |

The relationship between these tables forms a Star Schema, which is considered a best practice for analytical reporting because it improves model performance, simplifies calculations, and enables efficient filtering across multiple business dimensions.

### Dataset Description

**Fact_Cases**

This is the primary table used throughout the analysis. Each record represents a unique legal case.

The table includes important business attributes such as:

- Case ID, Client ID, Lawyer ID, Office City
- Open Date and Close Date
- Days Open, Billable Hours, Non-Billable Hours
- Court Appearances, Meetings, Documents Produced
- Revenue (EUR), Internal Costs (EUR), Profit (EUR), Profit Margin %
- Invoice Amount (EUR), Outstanding Balance (EUR)
- Client Satisfaction Score, Risk Score
- Lawyer Utilization %, Workload Index

This table forms the basis for nearly all calculations and visualizations within the dashboard.

**Dim_Case**

Contains descriptive information about each case, including Case Status (Open, Under Review, Negotiation, Court Proceedings, Pending Closure, Closed), Case Outcome (Won, Lost, Settled, Withdrawn, Ongoing), Case Complexity, Case Type, Practice Area, and Priority.

**Dim_Lawyer**

Contains descriptive information about each of the firm's 200 lawyers, including Gender, Age Group, Years Experience, Seniority (Associate, Senior Associate, Counsel, Partner), Department, and Employment Status.

**Dim_Client**

Contains descriptive information about each of the firm's 800 clients, including Industry, Company Size, Client Country, Client Region, Strategic Client Flag, and Client Since Year.

**Dim_Office**

Contains descriptive information about each of the firm's 15 offices, including Country, Region, Latitude, Longitude, and a Headquarters Flag (Riga is the firm's HQ).

**Dim_Date**

A standard calendar dimension supporting Year, Quarter, Month, Fiscal Year, and weekend/period-boundary flags, enabling time intelligence calculations across the model.

## Data Preparation and Transformation

Before developing the dashboard, the datasets were reviewed to ensure they were suitable for analysis. The preparation process involved importing the datasets into Power BI, validating data quality, establishing relationships between tables, and confirming that all fields were assigned the correct data types.

Although the dataset was relatively clean, several validation checks were performed to improve model reliability and analytical accuracy.

### Importing the Dataset into Power BI

The dataset was imported into Power BI Desktop from Excel. The following steps were performed:

- Opened Power BI Desktop.
- Selected Get Data from the Home ribbon.
- Chose Excel Workbook as the data source.
- Imported each sheet (Fact_Cases and the five dimension tables) individually.
- Reviewed each table within the Power Query Editor.
- Loaded the validated tables into the Power BI data model.

Once imported, relationships were established between the fact table and the dimension tables using their respective keys, and a Date Key was derived from Open Date to support the join to Dim_Date.

### Data Cleaning

The following data quality checks were performed before beginning the analysis:

- Verified that each case contained a unique Case ID, with zero duplicates found.
- Confirmed that numerical fields such as Revenue, Profit, and Billable Hours were correctly formatted as decimal values.
- Ensured that Open Date and Close Date were stored as Date data types.
- Verified that Client IDs, Lawyer IDs, and Office City values matched their corresponding dimension tables, with zero orphaned foreign keys found.
- Reviewed missing values across all columns.

One important observation was the presence of blank values in the Close Date column, affecting 40.4% of records (6,059 of 15,000). Rather than treating this as missing data, it was interpreted as a valid, conditional field: Close Date only applies to cases that have reached a final status, so blanks occur naturally for any case still Open, Under Review, in Negotiation, or in Court Proceedings.

A related observation was that cases in Pending Closure status already have a Close Date populated even though the case is not yet formally Closed. This is intentional in the dataset design, but it means Case Status, not Close Date presence, must be used as the definition of a completed case throughout the model.

No significant duplicate records or relationship inconsistencies were identified during the validation process.

### Data Modelling

A Star Schema was implemented to organize the data model. The Fact_Cases table serves as the central table, while the Case, Lawyer, Client, Office, and Date tables provide descriptive information used for slicing and filtering the data.

This modelling approach offers several advantages:

- Faster report performance.
- Reduced data redundancy.
- Simpler DAX calculations.
- Improved scalability for future enhancements.
- Easier maintenance and troubleshooting.

The relationships were configured as one-to-many relationships, with the dimension tables acting as lookup tables and Fact_Cases serving as the central fact table. This model supports interactive filtering across practice areas, offices, lawyer seniority, and client segments without duplicating case-level data.

## Data Analysis in Power BI

After preparing the data model, Power BI was used to develop measures that transformed raw case-level data into meaningful business metrics. These measures provide partners with quantitative insight into profitability, case outcomes, lawyer workload, and client value.

Data Analysis Expressions (DAX) were used extensively throughout the project to calculate KPIs, percentages, and performance indicators that could not be obtained directly from the raw dataset.

### DAX Measures Created

**Total Cases**
```dax
Total Cases = COUNTROWS(Fact_Cases)
```
*Purpose:* Counts all case records; the foundation measure most other counts and rates are built from.

*Business Value:* Base unit for every case-volume figure on the dashboard.

**Total Revenue**
```dax
Total Revenue = SUM(Fact_Cases[Revenue (EUR)])
```
*Purpose:* Calculates the total monetary value of all case revenue.

*Business Value:* Measures the overall scale of the firm's fee-generating activity and supports year-over-year growth tracking.

**Total Profit**
```dax
Total Profit = SUM(Fact_Cases[Profit (EUR)])
```
*Purpose:* Calculates total profit across all cases.

*Business Value:* Headline profitability figure used on the Overview KPI strip and the Clients page's Avg Profit per Client calculation.

**Profit Margin %**
```dax
Profit Margin % = DIVIDE([Total Profit], [Total Revenue], 0)
```
*Purpose:* Calculates firm-wide profit margin as a ratio of total profit to total revenue, rather than averaging the pre-calculated per-case percentage column.


**Total Invoice Amount**
```dax
Total Invoice Amount = SUM(Fact_Cases[Invoice Amount (EUR)])
```
*Purpose:* Calculates total amount invoiced to clients.

*Business Value:* Denominator for Outstanding Balance %, and the basis for the "€2.8B total invoiced" Overview subtitle.

**Total Outstanding Balance / Outstanding Balance %**
```dax
Total Outstanding Balance = SUM(Fact_Cases[Outstanding Balance (EUR)])

Outstanding Balance % =
DIVIDE([Total Outstanding Balance], [Total Invoice Amount], 0)
```
*Purpose:* Calculates the total unpaid portion of invoiced revenue, and that amount as a share of total invoicing.

*Business Value:* Gives partners and Finance a direct view of collections exposure alongside revenue and profit, rather than treating billing as a separate process from performance reporting.

**Won Cases / Completed Cases / Win Rate %**
```dax
Won Cases =
CALCULATE(
    [Total Cases],
    Dim_Case[Case Status] = "Closed",
    Dim_Case[Case Outcome] = "Won"
)

Completed Cases =
CALCULATE(
    [Total Cases],
    Dim_Case[Case Status] = "Closed"
)

Win Rate % = DIVIDE([Won Cases], [Completed Cases])
```
*Purpose:* Calculates the proportion of formally Closed cases that were Won.

*Business Value:* Gives partners a clean, reconciled view of case success, using Case Status as the consistent definition of "completed" throughout.

**Active Cases**
```dax
Active Cases =
CALCULATE(
    [Total Cases],
    Dim_Case[Case Status] <> "Closed"
)
```
*Purpose:* Counts every case that has not yet reached a formally Closed status (Open, Under Review, Negotiation, Court Proceedings, or Pending Closure).

*Business Value:* Gives partners a live view of current caseload volume, distinct from the historical Closed-case population used for Win Rate.

**Avg Case Duration**
```dax
Avg Case Duration = AVERAGE(Fact_Cases[Days Open])
```
*Purpose:* Calculates average case duration across the portfolio, using the pre-calculated Days Open column so active cases (which have no Close Date) are still included.

*Business Value:* Powers the Performance page's Average Case Duration KPI card.

**Avg Billable Hours**
```dax
Avg Billable Hours = AVERAGE(Fact_Cases[Billable Hours])
```
*Purpose:* Calculates average billable hours per case.

*Business Value:* Powers the Performance page's Average Billable hr KPI card.

**Total Billable Hours / Total Non-Billable Hours / Non-Billable Hours %**
```dax
Total Billable Hours = SUM(Fact_Cases[Billable Hours])
Total Non-Billable Hours = SUM(Fact_Cases[Non-Billable Hours])

Non-Billable Hours % =
DIVIDE([Total Non-Billable Hours], [Total Billable Hours] + [Total Non-Billable Hours], 0)
```
*Purpose:* Total Billable Hours powers the lawyer-level table's Billable column; Non-Billable Hours % calculates the share of all logged hours that are non-billable.

*Business Value:* Total Billable Hours supports per-lawyer productivity comparison; Non-Billable Hours % highlights internal time not directly recovered through client billing.

**Non-Billable Hours Text**
```dax
Non-Billable Hours Text =
FORMAT([Non-Billable Hours %], "0%") & " of hours non-billable"
```
*Purpose:* Formats the non-billable hours ratio as a display-ready subtitle string.

*Business Value:* Gives the Billable Hours KPI card a companion metric instead of repeating the utilization figure shown elsewhere on the page.

**Avg Lawyer Utilization % (by seniority)**
```dax
Avg Lawyer Utilization % = AVERAGE(Fact_Cases[Lawyer Utilization %])

Avg Utilization - Partners =
CALCULATE(AVERAGE(Fact_Cases[Lawyer Utilization %]), Dim_Lawyer[Seniority] = "Partner")

Avg Utilization - Associates =
CALCULATE(AVERAGE(Fact_Cases[Lawyer Utilization %]), Dim_Lawyer[Seniority] = "Associate")
```
*Purpose:* Calculates average lawyer capacity utilization, firm-wide and by seniority tier.

*Business Value:* Surfaces workload imbalance across seniority levels, directly supporting the firm's resource allocation question.

**Utilization Spread Text**
```dax
Utilization Spread Text =
"Partner " & FORMAT([Avg Utilization - Partners], "0%") &
" | Associate " & FORMAT([Avg Utilization - Associates], "0%")
```
*Purpose:* Formats the Partner-versus-Associate utilization comparison as a single ready-to-display string.

*Business Value:* Powers the KPI card subtitle on the Performance page, surfacing the seniority gap directly under the headline utilization figure.

**Avg Workload Index**
```dax
Avg Workload Index = AVERAGE(Fact_Cases[Workload Index])
```
*Purpose:* Calculates average case-load intensity per lawyer.

*Business Value:* Powers the lawyer-level table's Workload column and the Utilization vs Workload scatter visual on the Performance page.

**Total Clients**
```dax
Total Clients = DISTINCTCOUNT(Fact_Cases[Client ID])
```
*Purpose:* Counts distinct clients represented in the current filter context.

*Business Value:* Denominator for Avg Profit per Client; also powers the "800 Total Clients" subtitle on the Clients page.

**Strategic Client Revenue / Strategic Revenue Share %**
```dax
Strategic Client Revenue =
CALCULATE([Total Revenue], Dim_Client[Strategic Client Flag] = "Yes")

Strategic Revenue Share % =
DIVIDE([Strategic Client Revenue], [Total Revenue], 0)
```
*Purpose:* Isolates revenue generated by clients flagged as strategic accounts, and expresses it as a share of total firm revenue.

*Business Value:* Powers the Clients page's Strategic Client Revenue KPI card and the Overview page's "20.0% from strategic clients" subtitle.

**Avg Client Satisfaction**
```dax
Avg Client Satisfaction = AVERAGE(Fact_Cases[Client Satisfaction Score])
```
*Purpose:* Calculates average client satisfaction across all cases.

*Business Value:* Powers the Clients page's Average Satisfaction KPI card.

**Avg Profit per Client / Median Profit per Client**
```dax
Avg Profit per Client = DIVIDE([Total Profit], [Total Clients], 0)

Median Profit per Client =
MEDIANX(VALUES(Fact_Cases[Client ID]), CALCULATE([Total Profit]))
```
*Purpose:* Calculates average and median profit generated per client.

*Business Value:* Powers the Clients page's Average Profit per Client KPI card and its "Median/client" subtitle; the gap between the two (€1.99M average vs €1,650,473 median) is what reveals that a small number of high-value clients are pulling the average upward.

**Selected KPI (dynamic trend measure)**
```dax
Selected KPI =
SWITCH(
    SELECTEDVALUE('KPI Selector'[KPI]),
    "Total Revenue", [Total Revenue],
    "Total Profit", [Total Profit],
    "Profit Margin", [Profit Margin % (Weighted)],
    "Active Cases", [Active Cases]
)
```
*Purpose:* Uses a disconnected KPI Selector table so a single trend chart, KPI card set, and map on the Overview page can all switch between Total Revenue, Total Profit, Profit Margin, and Active Cases without duplicating visuals.

*Business Value:* Lets partners explore firm performance across multiple KPIs from one interactive view instead of navigating between separate charts for each metric.

## Dashboard Development

The dashboard was designed to give partners a clear path from firm-wide performance into practice area, lawyer, and client-level detail. Rather than presenting every metric on a single page, the report is divided into three dedicated pages, each focusing on a specific business function, with global slicers (Year/Quarter, Office City, Practice Area) synced across all three.

### Overview

<img width="864" height="484" alt="Image" src="https://github.com/user-attachments/assets/ec94b694-7729-4b03-a51a-8de06b35f932" />

---
The Overview page provides a high-level summary of the firm's financial and operational performance. The primary objective of this page is to answer the question: *"How is the firm performing overall?"*

Key Performance Indicators displayed include:
- Total Revenue
- Total Profit
- Outstanding Balance
- Active Cases

Supporting visualizations include:
- Revenue trend over time, alongside Profit Margin %
- Revenue by Practice Area
- Revenue by Case Outcome
- Revenue by Office City (map)

This page enables partners to quickly identify firm-wide performance trends and drill into whichever area needs attention.

### Performance

<img width="863" height="483" alt="Image" src="https://github.com/user-attachments/assets/3ec9390e-1df9-4487-84a8-9e4f80fc998e" />

---
The Performance page was designed to support practice group leads and operations management by providing a detailed view of lawyer productivity, workload, and case outcomes. The primary objective of this page is to answer the question: *"Where is capacity being used well, and where is it not?"*

Key Performance Indicators:
- Average Lawyer Utilization
- Average Billable Hours
- Average Case Duration
- Win Rate %

Supporting Visualizations:
- Lawyer-level performance table (cases, win rate, workload, utilization, profit, billable hours)
- Utilization vs Workload scatter, by seniority
- Utilization by Seniority

Together, these visuals give a complete picture of how lawyer capacity is being allocated and where workload imbalance exists.

### Clients

<img width="862" height="484" alt="Image" src="https://github.com/user-attachments/assets/ca20f13c-0b2c-4e40-81b0-793f5f3efc93" />

---
The Clients page focuses on client value, revenue concentration, and satisfaction. The primary objective of this page is to answer the question: *"Which clients and relationships matter most, and how satisfied are they?"*

Key Performance Indicators:
- Average Satisfaction
- Outstanding Balance
- Strategic Client Revenue
- Average Profit per Client

Supporting Visualizations:
- Revenue by Client Industry
- Revenue by Client Type (Strategic vs Non-Strategic)
- Client-level detail table (Revenue, Profit, Satisfaction, Outstanding Balance)

These visualizations help partners identify which client relationships carry the most value and where satisfaction or collections risk may be building.

## Insights from the Data Analysis

### Overview Insights

**Firm Performance**

The dashboard shows the firm processed 15,000 cases across the reporting period, generating €2.80 billion in total revenue and €1.59 billion in profit, a firm-wide profit margin of 56.8%. Of the 15,000 cases, 8,118 remain active (Open, Under Review, Negotiation, Court Proceedings, or Pending Closure), while 6,882 have reached a formally Closed status. Average case duration stands at 258 days.

**Practice Area Performance**

Regulatory Compliance is the firm's largest revenue driver at €433.8 million, narrowly ahead of Mergers & Acquisitions at €423.4 million and Litigation at €380.0 million. Corporate Law (€347.1 million) and Intellectual Property (€308.1 million) round out the top five. Family Law (€100.7 million) and Real Estate Law (€153.0 million) trail well behind, together representing the smallest share of the ten-practice-area mix.

**Office Performance**

The Frankfurt office stands out on profitability, generating €365.6 million in revenue at a 57.0% margin, slightly ahead of the firm average of 56.8%. Clients headquartered in Germany carry a comparable weighted margin of 55.7% on €102.3 million in revenue, suggesting the strength is driven by the office's overall case mix rather than any single large client relationship.

**Case Outcome Revenue Concentration**

Revenue splits fairly evenly across outcomes by case count, but not by value: Won cases account for 27.9% of total revenue (€782.1 million), Settled for 27.4% (€767.2 million), and Ongoing for 26.5% (€742.6 million), while Lost cases represent just 12.6% (€354.5 million) and Withdrawn only 5.6% (€156.8 million). Won and Settled cases carrying a disproportionate share of revenue relative to Lost and Withdrawn cases suggests the firm's higher-value engagements are also its more successful ones.

### Performance Insights

**Utilization by Seniority**

Firm-wide average lawyer utilization sits at 20.5% of estimated annual capacity, but this figure masks a wide gap by seniority. Partners average 43.8% utilization, close to three times the 15.3% seen among Associates, with Counsel (28.0%) and Senior Associates (20.9%) in between. Average billable hours per case stand at 140, with 13.1% of all logged hours across the firm being non-billable.

This gap is worth treating as a resourcing signal rather than background detail. Partners are carrying a disproportionate share of billable work relative to their capacity, while Associate capacity appears comparatively underused across the portfolio, a pattern with direct implications for both burnout risk at the senior end and development opportunity at the junior end.

**Win Rate**

The firm's win rate stands at 36.3%, calculated as 2,495 Won cases against 6,882 formally Closed cases (1,295 Lost, 2,338 Settled, 754 Withdrawn making up the remainder). This is the figure that should be used consistently across partner reporting, since it is reconciled directly against the underlying Closed-case population.

**Lawyer-Level Analysis**

The firm-wide utilization gap by seniority is largely explained by case assignment, not effort: Associates handle 71.3% Low-complexity and 28.7% Medium-complexity cases exclusively, with zero High or Critical cases, while Partners handle only High (46.9%) and Critical (53.1%) complexity cases. That structural split shows up directly in profit per case, Associates average €13,307 profit per case versus €767,708 for Partners, a 58x difference driven by case tier rather than individual performance. Win rate follows the same pattern: Partner 45.3%, Counsel 42.8%, Senior Associate 37.6%, Associate 32.0%.

The firm's five highest-profit lawyers are all Partners, led by Javier Smit (€41.0M profit across 56 cases, 41.7% average utilization) and Matthias Novak (€38.5M, 49 cases). One name breaks the seniority pattern worth calling out: Sebastian Rodriguez, a Counsel, generated €36.6M in profit across 87 cases, in range with the Partner cohort despite being one tier below it, worth reviewing as a promotion or compensation signal.

Even at the very top of the workload distribution, utilization stays well short of full capacity. The five lawyers carrying the heaviest average workload index (2.6 to 2.85) are all Partners, and none of them exceed 47.2% utilization, Thomas Eriksson, the single highest-utilization lawyer in the firm, still sits under half of estimated annual capacity. This matters for how the caseload-rebalancing recommendation should be framed: this is not a small group of Partners already at their limit, headroom exists even among the firm's busiest lawyers, which makes redistributing work toward Associates a lower-risk change than it would be in a firm already running its top performers close to capacity.

Two individuals stand out as a genuine outlier within their own peer group, not just relative to Partners. Camille Eriksson and Lars Müller, both Associates, post a 13.9% win rate on 82 and 69 cases respectively, well below the 32.0% Associate average, despite handling a similar Low/Medium complexity mix to their peers. Their case volume is high but their profit contribution is low (€1.22M and €1.05M respectively, versus a typical Associate generating a comparable amount from roughly a third as many cases). This combination, high volume, low win rate, low profit per case, is worth a direct performance conversation rather than being absorbed into the firm-wide seniority averages, where it is currently invisible.

### Client Insights

**Client Value and Concentration**

132 of the firm's 800 clients (16.5%) are flagged as strategic accounts, and they generate €560.3 million in revenue, exactly 20.0% of total firm revenue. The remaining 668 non-strategic clients generate the larger share of firm revenue in aggregate, €2.24 billion, or 80.0% of the total, simply because there are five times as many of them.

On a per-client basis, however, strategic clients remain the more valuable relationship: €4.24 million average revenue per strategic client versus €3.36 million per non-strategic client, alongside a slightly higher profit margin (57.3% versus 56.7%) and slightly higher satisfaction (6.67 versus 6.63). Average profit per client across the firm stands at €1.99 million, with a median of €1,650,473, meaning the average is being pulled upward by a smaller number of especially high-value relationships rather than reflecting a typical client.

**Client Satisfaction and Collections**

Average client satisfaction across all cases is 6.64 out of 10. Outstanding balances stand at €773.4 million, 27.6% of the €2.80 billion invoiced to date, a figure worth monitoring alongside satisfaction, since unresolved billing can be a leading indicator of relationship strain even when case outcomes are otherwise favorable.

**Client-Level Analysis**

Revenue concentration among individual clients is moderate rather than extreme: the top 10 clients by revenue together generate €114.5 million, just 4.1% of total firm revenue, and the top 20% of clients (160 of 800) account for 40.6% of revenue. No single relationship dominates the book, which limits single-client concentration risk but also means growth has to come from broad account management rather than a handful of key relationships.

Seven of the ten highest-revenue clients in the firm are not flagged as strategic accounts. Baltic Meridian AG is the single highest-revenue client in the entire portfolio at €16.6 million, Media & Entertainment, non-strategic, followed by Iberian Western Holdings (€14.1 million, Energy, non-strategic) and Vertex Crestline Consulting (€10.4 million, Healthcare, non-strategic). This is the concrete evidence behind the earlier recommendation to review the non-strategic base: Baltic Meridian AG alone generates more revenue than several clients that do carry the strategic flag, and is the clearest individual candidate for re-flagging.

Eight clients combine above-median revenue with satisfaction below 6.0, a pattern worth treating as an early relationship-risk list rather than a coincidence. Crestline Summit Enterprises leads this group at €9.7 million revenue against a 5.96 satisfaction score, followed by Pacific Apex Consulting (€8.7 million, 5.78) and Horizon Capital Associates (€8.4 million, 5.96). None of these clients are currently flagged strategic, so none are likely receiving the account-level attention their revenue would otherwise justify.

Outstanding balance is not evenly spread: as a share of each client's own revenue, it ranges from 1.6% to 81.3% across the 800 clients, with a median of 24.4%. Western Baltic SA carries both the highest absolute outstanding balance (€5.66 million, 57.2% of its own revenue) and a strong satisfaction score (6.88), suggesting the delay is procedural rather than a sign of dissatisfaction, worth a direct billing follow-up rather than a relationship review. Alpine Crestline Technologies, one of the few Strategic-flagged clients carrying a large balance (€5.33 million, 43.1% of its revenue), is worth prioritizing precisely because of its strategic status.

## Business Recommendations

**1. Rebalance Caseload from Partners Toward Associates and Senior Associates**

*Observation:* Partners average 43.8% utilization versus 15.3% for Associates, a gap of nearly three times.

*Recommendation:* Redistribute a portion of Partner caseload, particularly in high-volume practice areas, toward Associates and Senior Associates.

*Expected Benefit:* Improved capacity utilization across junior tiers; reduced Partner overload risk; supports Associate development and retention.

**2. Prioritize Collections on the Outstanding Invoice Balance**

*Observation:* €773.4 million, 27.6% of invoiced revenue, remains uncollected.

*Recommendation:* Introduce a structured collections review, prioritizing the largest outstanding balances identified in the client-level table.

*Expected Benefit:* Faster cash conversion; reduced days-sales-outstanding; improved working capital position.

**3. Deepen Strategic Relationships While Reviewing the Non-Strategic Base for Under-Flagged Value**

*Observation:* Strategic clients generate more revenue per relationship (€4.24M average versus €3.36M), but the 668 non-strategic clients still account for €2.24 billion, 80% of total firm revenue, in aggregate. Some non-strategic clients are likely generating strategic-level value without carrying the flag.

*Recommendation:* Build account-specific engagement plans for the highest-profit clients already identified within the strategic tier, and separately, review the non-strategic client table for individual accounts whose revenue and profit rival the strategic average, as candidates for re-flagging.

*Expected Benefit:* Higher retention and expansion revenue among top-tier clients; ensures high-value relationships are not overlooked simply because they sit in the larger, non-strategic pool.

**4. Review Lower-Revenue Practice Areas for Strategic Fit**

*Observation:* Family Law (€100.7M) and Real Estate Law (€153.0M) trail well behind the top five practice areas.

*Recommendation:* Make a deliberate decision to either invest in growing these practice areas or reallocate the capacity currently assigned to them toward higher-performing areas such as Regulatory Compliance and Mergers & Acquisitions.

*Expected Benefit:* Clearer capital and staffing allocation across practice areas; avoids capacity sitting in underperforming segments by default.


## Conclusion

This project demonstrates how Business Intelligence can be applied to transform raw legal case data into actionable business insight.

Using Power BI, a dimensional data model, and DAX calculations, an interactive dashboard was developed to monitor firm-wide profitability, case outcomes, lawyer workload, and client value across LexEuropa's 15 European offices.

The analysis found a firm that is fundamentally strong at the aggregate level, with a healthy 56.8% profit margin and revenue concentrated in well-understood, high-performing practice areas, alongside clear, well-defined opportunities sitting just beneath the headline numbers. Lawyer utilization is unevenly distributed by seniority. Revenue is meaningfully concentrated in a strategic client tier that is already generating outsized value. Outstanding balances represent a material, addressable collections opportunity.

That concentration is the most useful takeaway from this analysis: each of the five recommendations above is a targeted, measurable action that a single team can own, rather than a broad transformation effort, which means the path from this dashboard to real operational impact is short.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Power BI Desktop | Data modelling, DAX calculations, dashboard development, and visualization |
| Power Query | Data import, cleaning, and transformation |
| DAX (Data Analysis Expressions) | Creation of KPIs, calculated measures, and analytical metrics |
| Excel Source File | Fact and dimension table storage |
| Star Schema Modelling | Efficient relational data model for reporting |

## Author

**Eucharia Chibuike N.**
Data Analyst | Power BI | SQL | Excel | Python

If you found this project interesting or have suggestions for improvement, feel free to connect or reach out. Feedback and collaboration are always welcome.

