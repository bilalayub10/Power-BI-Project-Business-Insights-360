# Business Insights 360

## Project Overview

AtliQ Hardware is at a pivotal point in its growth. Once a fast-rising player in the global electronics market, the company began facing serious setbacks due to intuition-based decision making. The most critical: a failed expansion into Latin America, where physical stores were opened based on limited surveys — leading to significant financial losses.

To illustrate the gap: From 2019 to 2021, Latin America's net sales grew from **$0.83M to $3.16M** — a **280% increase**, yet still far behind regions like APAC (**$441.98M**) and EU (**$177.94M**). Worse, LATAM’s **gross margin % fell** from **42.32% to 37.54%**, signaling reduced profitability despite the growth.

Meanwhile, competitors like Dell — equipped with mature analytics teams — were making faster, smarter moves. The writing was on the wall: AtliQ needed to shift from gut-driven decisions to a **data-first culture**.

This Power BI project is AtliQ’s first major step in that transformation. The goal was clear:
- Empower leadership with real-time insights
- Build interactive dashboards for cross-functional teams
- Replace Excel-based processes with scalable data models

I led the design and development of a comprehensive Power BI solution that aligned directly with the company’s business units — Finance, Sales, Marketing, and Supply Chain — helping them answer not just “what happened,” but “why,” “how,” and “what next.”

This wasn’t just about building visuals. It was about **building trust in data** — and a system to drive decisions with confidence.

## Project Charter

### Key Stakeholders

- **Product Owner** – Business Sponsor and key decision-maker
- **CEO** – Strategic driver for data transformation
- **Data & Analytics Lead** – Owner of data structure and validation
- **IT Lead** – Manages system infrastructure and Power BI service

---

### Project Objectives

- Enable **quick insights** across markets and departments
- Transition from intuition to **data-driven decision making**
- Support business functions in **daily operational analysis**

---

### Success Measures

- A functional, **validated dashboard** with core business metrics
- Dashboard is actively used in meetings and decision making for:
  - Customer negotiations
  - New product launches
  - Marketing campaigns
  - Finance and budgeting

---

### Timeline

- **8 weeks** total duration
- **MVP delivered in 4 weeks** for UAT testing and stakeholder feedback

---

### Hopes vs. Fears

| Hopes                                  | Fears                                |
|----------------------------------------|--------------------------------------|
| Data-driven decision making            | Data correctness & completeness      |
| Effective communication via insights   | Feature creep                        |
| Reduced manual effort                  | Lack of adoption                     |
| Transparency across departments        | Misalignment in expectations         |

---

### Expectations & Mockups

- Provided via Excel from Product Owner
- Views to be built:
  - Finance View
  - Sales View
  - Marketing View
  - Supply Chain View
  - Executive View
- Each view came with:
  - **Mockup layouts**
  - **Benchmark figures** for data validation

## Data Understanding & Model Design

To build a reliable reporting solution, it’s critical to understand the underlying data structure and model it efficiently. AtliQ’s data was sourced from two SQL databases and several Excel files — a blend of transactional and dimensional data, designed for analytical workloads.

### Data Sources

**SQL Database - `gdb041`:**
- **`dim_customer`** (209 records | 5 columns): Customer attributes across 27 markets and 74 unique customers. Includes platform type (E-Commerce or Brick & Mortar) and sales channel (Retailer, Direct, Distributor).
- **`dim_market`** (27 records | 3 columns): Contains region, market and sub-zone mappings (APAC, EU, LATAM, etc.).
- **`dim_product`** (397 records | 6 columns): Product hierarchy by division, segment, category, and variant.
- **`fact_forecast_monthly`** (1,885,941 records | 4 columns): Forecasted product demand per customer per month. Dates are normalized to month start for time-series analysis.
- **`fact_sales_monthly`** (1,885,941 records | 4 columns): Actual monthly sales data at the same granularity as the forecast table, enabling direct comparison.

**SQL Database - `gdb056`:**
- **`freight_cost`** (135 records | 4 columns): Market-level logistics and freight costs by fiscal year.
- **`manufacturing_cost`** (1,197 records | 3 columns): Manufacturing cost per product per year.
- **`pre_invoice_deductions`** (1045 records | 3 columns): Discount percentages applied before invoicing, organized by customer_code and fiscal_year.
- **`post_invoice_deductions`** (2,063,076 records | 5 columns): Post-sale deductions such as discounts or promotional rebates.

**Excel Files:**
- **`market_share`** (737 records | 6 columns): Market share data across sub-zones, categories, and manufacturers with total sales by fiscal year..
- **`operational_expense`** (113 records | 4 columns): Market-wise OPEX data for financial analysis.
- **`ns_gm_target`** (321 records | 5 columns): Net Sales, Gross Margin and Net Profit targets for markets.

### Data Model Design

A **snowflake schema** was implemented to ensure normalization and performance optimization. Fact tables are linked to their respective dimension tables using matching columns, and time intelligence was enabled using a custom **Date table** created in Power Query.

> **Note:** Data granularity is monthly, and the fiscal year for AtliQ starts in **September** and ends in **August**, which was factored into time-based calculations and visuals.

This model architecture ensures scalability, flexibility in filtering, and robust DAX performance — essential for responsive dashboards and fast decision-making.

## Dashboard Design & Implementation

The core goal of this dashboard was to empower AtliQ Hardware’s leadership and department heads to make **faster, smarter, and cross-functional decisions**. With scattered data across Excel files and SQL tables, business teams had no single source of truth.

This section outlines how I translated business requirements into **interactive Power BI dashboards**, built around usability, data accuracy, and performance.

### Home View

The **Home View** serves as the strategic entry point into the entire Power BI reporting system. Designed with both **clarity and speed of navigation** in mind, this screen enables users from different departments to instantly access dashboards relevant to their functional area.
![Home View](path-to-home-gif.gif)


### Finance View 

The **Finance View** provides a comprehensive and interactive **Profit & Loss Statement**, empowering finance teams to analyze performance across multiple dimensions with speed and precision.
![Finance View](path-to-finance-gif.gif)

### Sales View 

The **Sales View** is designed for **Sales Managers, Analysts, and Business Leaders** to monitor customer performance, identify margin risks, and optimize sales strategy. It enables precise, interactive exploration of **Net Sales** and **Gross Margin** across key customer segments and geographies.
![Sales View](path-to-sales-gif.gif)

### Marketing View

The **Marketing View** helps the marketing team analyze product performance across segments by comparing Net Sales, Gross Margin %, and Net Profit %. It’s designed to surface underperforming product lines and identify key areas of concern or opportunity — all at a glance.
![Marketing View](path-to-marketing-gif.gif)

### Supply Chain View

The **Supply Chain View** provides a comprehensive view of supply chain performance, focusing on forecast accuracy, error trends, and key metrics by customer and product. It enables stakeholders to monitor and optimize supply chain operations effectively.
![Supply Chain View](path-to-supply-chain-gif.gif)





    


