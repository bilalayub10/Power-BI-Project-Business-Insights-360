# Business Insights 360

## Project Overview

AtliQ Hardware is at a pivotal point in its growth. Once a fast-rising player in the global electronics market, the company began facing serious setbacks due to intuition-based decision making. The most critical: a failed expansion into Latin America, where physical stores were opened based on limited surveys — leading to significant financial losses.

To illustrate the gap: From 2019 to 2021, Latin America's net sales grew from **$0.83M to $3.16M** — a **280% increase**, yet still far behind regions like APAC (**$441.98M**) and EU (**$177.94M**). Worse, LATAM’s **gross margin % fell** from **42.32% to 37.54%**, signaling reduced profitability despite the growth.

Meanwhile, competitors like Dell — equipped with mature analytics teams — were making faster, smarter moves. The writing was on the wall: AtliQ needed to shift from gut-driven decisions to a **data-first culture**.

This Power BI project is AtliQ’s first major step in that transformation. The goal was clear:
- Empower leadership with real-time insights.
- Build interactive dashboards for cross-functional teams.
- Replace Excel-based processes with scalable data models.

[**Live Dashboard Link**](https://app.powerbi.com/view?r=eyJrIjoiMzE2M2Q1MWYtODg2MS00M2NjLTg4NjUtMGIwMDJhN2MyY2NiIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9) - Explore the dashboard and interact with the reports.


I led the design and development of a comprehensive Power BI solution that aligned directly with the company’s business units — Finance, Sales, Marketing, and Supply Chain — helping them answer not just “what happened,” but “why,” “how,” and “what next.”

This wasn’t just about building visuals. It was about **building trust in data** — and a system to drive decisions with confidence.

## AtliQ Hardware Business Model

AtliQ Hardware is an imaginary global company specializing in manufacturing and selling high-quality hardware products, including PCs, keyboards, printers, and other peripherals. Similar to industry leaders such as HP and Dell, AtliQ designs and produces hardware and distributes it through multiple sales channels.
AtliQ's business operates through three primary channels:

Retailers: This includes both Brick & Mortar (physical retail stores like BestBuy, Croma, etc.) and E-Commerce (online stores such as Amazon, Flipkart, etc.). These retailers act as intermediaries, purchasing AtliQ products in bulk and selling them directly to the end consumers.

Direct Sales: AtliQ operates its own stores, both online and offline, where they sell directly to consumers. This allows them to control the customer experience and build direct relationships with their user base.

Distributors: In certain regions, AtliQ works with distributors who purchase hardware from them and sell it to various retailers across their respective markets.

AtliQ’s customers fall into two main categories:

Brick & Mortar Stores: Physical stores where consumers can walk in, experience products, and make purchases in person.

E-Commerce Stores: Online platforms where consumers can browse and purchase products digitally.

## Project Charter

### Key Stakeholders

- **Product Owner** – Business Sponsor and key decision-maker
- **CEO** – Strategic driver for data transformation
- **Data & Analytics Lead** – Owner of data structure and validation
- **IT Lead** – Manages system infrastructure and Power BI service

---

### Project Objectives

- Enable **quick insights** across markets and departments.
- Transition from intuition to **data-driven decision making**.
- Support business functions in **daily operational analysis**.

---

### Success Measures

- A functional, **validated dashboard** with core business metrics.
- Dashboard is actively used in meetings and decision making for:
  - Customer negotiations
  - New product launches
  - Marketing campaigns
  - Finance and budgeting

---

### Timeline

- **8 weeks** total duration.
- **MVP delivered in 4 weeks** for UAT testing and stakeholder feedback.

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

- Provided via Excel from Product Owner.
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
- **`dim_market`** (27 records | 3 columns): Contains region, market and sub-zone mappings.
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

<img src = "https://github.com/user-attachments/assets/9ebbaa73-6b29-4d70-a074-bb7e7c951f0a" class="center">


## Dashboard Design & Implementation

To support AtliQ Hardware’s shift toward a data-driven culture, I designed and implemented a centralized Power BI dashboard solution. The dashboard is structured around five core business functions — **Finance**, **Sales**, **Marketing**, **Supply Chain**, and **Executive Management** — each with its own interactive view to support faster and smarter decision-making.

### Overview of Dashboard

<img src = "https://github.com/user-attachments/assets/d8efd614-6309-41eb-9038-b87fdadd18fb" class="center">


We’ll now walk through each view, starting with the Home View and moving into individual department-specific views.

### Home View

The **Home View** serves as the strategic entry point into the entire Power BI reporting system. Designed with both **clarity and speed of navigation** in mind, this screen enables users from different departments to instantly access dashboards relevant to their functional area.

<img src = "https://github.com/user-attachments/assets/49e02678-4af1-41c9-828d-e667a5f548ec" class="center">

### Finance View 

The **Finance View** provides a comprehensive and interactive **Profit & Loss Statement**, empowering finance teams to analyze performance across multiple dimensions with speed and precision.

<img src = "https://github.com/user-attachments/assets/cee58785-3ae8-4006-9ef1-d4551771064b" class="center">


### Sales View 

The **Sales View** is designed for **Sales Managers, Analysts, and Business Leaders** to monitor customer performance, identify margin risks, and optimize sales strategy. It enables precise, interactive exploration of **Net Sales** and **Gross Margin** across key customer segments and geographies.

<img src = "https://github.com/user-attachments/assets/9387ad6d-8cf9-4ae7-bcdd-b247ee500936" class="center">

### Marketing View

The **Marketing View** helps the marketing team analyze product performance across segments by comparing Net Sales, Gross Margin %, and Net Profit %. It’s designed to surface underperforming product lines and identify key areas of concern or opportunity — all at a glance.

<img src = "https://github.com/user-attachments/assets/7ab96c13-2f1b-435a-8681-184eaad30128" class="center">

### Supply Chain View

The **Supply Chain View** provides a comprehensive view of supply chain performance, focusing on forecast accuracy, error trends, and key metrics by customer and product. It enables stakeholders to monitor and optimize supply chain operations effectively.

<img src = "https://github.com/user-attachments/assets/19925079-7050-44ca-8aa3-3c45f98c3774" class="center">

### Executive View
The **Executive View** provides a holistic view of business performance, focusing on key financial metrics, customer and product insights, and regional contributions. It is designed to empower executives with actionable data for strategic decision-making.

<img src = "https://github.com/user-attachments/assets/59567f5a-e306-43ae-b217-4023bf7270b1" class="center">

[**Live Dashboard Link**](https://app.powerbi.com/view?r=eyJrIjoiMzE2M2Q1MWYtODg2MS00M2NjLTg4NjUtMGIwMDJhN2MyY2NiIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9) - Explore full dashboard and interact with the reports.

## Key Learnings

This project helped me deepen both my technical expertise and my strategic thinking as a Power BI developer. Below are the critical skills & techniques I learned:

### Data Modeling & Preparation
- Designed an efficient snowflake schema for analytical performance and scalability.
- Created custom Date tables using M language to support time intelligence.
- Understood dimensional vs. fact tables, enabling better data relationships.
- Validated and reconciled data across multiple sources (SQL + Excel) to ensure accuracy.

### DAX & Visual Design
- Wrote robust DAX measures and calculated columns to drive KPIs and comparisons.
- Used the `DIVIDE()` function to safely handle division and avoid runtime errors.
- Applied dynamic titles and conditional formatting for contextual insights.
- Implemented KPI indicators, icon-based visuals, and variance ranges to highlight performance.

### UX & Interactivity
- Created bookmark-based toggles to switch seamlessly between different visuals.
- Used buttons for page navigation for a better user experience.

### Power BI Service & Deployment
- Published dashboards to Power BI Service.
- Configured data refresh via personal gateway for near real-time updates.
- Set up Power BI Apps, collaborated through workspaces, and managed access controls.

### Project Strategy & Execution
- Learned to ask the right business questions before modeling.
- Prioritized simplicity and speed for executive-level usability.
- Practiced data validation techniques to build stakeholder trust in the output.

## Tools and Technologies

- **Power BI Desktop**: For ETL (Extract, Transform, Load), data modeling, data visualization and dashboard creation.
- **MySQL**: For importing and querying data from the MySQL database.
- **DAX**: For custom calculations and performance metrics.
- **M Language (Power Query)**: For data transformation and custom Date table creation.
- **Excel**: For importing data, performing data validation and establishing benchmark figures.
- **Power BI Service**: For dashboard deployment and sharing.







    


