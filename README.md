# 📊 Supply Chain Analytics | Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-Analytics-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Measures-1F4E78?style=for-the-badge)
![Data Analytics](https://img.shields.io/badge/Data%20Analytics-Business%20Intelligence-0F6B78?style=for-the-badge)
![Supply Chain](https://img.shields.io/badge/Domain-Supply%20Chain-00A6A6?style=for-the-badge)

---

## 📌 Project Overview

The **Supply Chain Analytics** is an end-to-end **Power BI portfolio project** developed to analyze procurement spend, supplier performance, quality, risk, and logistics delivery performance.

The dashboard transforms operational procurement and logistics data into an interactive **3-page business intelligence solution** that enables stakeholders to monitor KPIs, identify performance gaps, understand variance drivers, and make data-driven decisions.

The project follows a business-first analytical approach:

**Procurement Data → Data Modeling → DAX Measures → KPI Development → Interactive Dashboard → Business Insights → Recommendations**

The dashboard is designed to provide a complete business story across:

- **Procurement Cost Control**
- **Supplier Performance**
- **Supplier Risk**
- **Purchase Price Variance**
- **Quality Performance**
- **Delivery Reliability**
- **Logistics Cost**
- **Carrier & Transport Performance**

---

## 🎯 Business Problem

The client operates across procurement and logistics functions with data distributed across multiple operational sources, including purchase orders, supplier information, shipment records, quantity logs, carrier data, warehouse information, and monthly procurement targets.

This fragmented data environment makes it difficult for management to quickly:

- Compare actual procurement spend against monthly targets.
- Identify unfavorable supplier pricing movements.
- Evaluate supplier delivery and quality performance.
- Monitor supplier risk exposure.
- Identify the major drivers of delivery delays.
- Analyze freight costs across carriers and transport modes.
- Monitor logistics performance against SLA commitments.
- Obtain a consolidated executive view of supply chain performance.

### Business Goal

Build a clean, interactive Power BI dashboard that replaces scattered operational checks with a centralized analytical solution supporting:

**Executive Review → Supplier Decisions → Procurement Cost Control → Logistics Improvement**

---

## ❓ Business Questions

The dashboard was designed to answer the following business questions:

1. How does actual procurement spend compare with the monthly target?
2. Which product categories contribute most to spend variance?
3. Which suppliers demonstrate stronger or weaker pricing, quality, and delivery performance?
4. Where are the major Purchase Price Variance (PPV) drivers?
5. What is the overall On-Time Delivery performance?
6. Which carriers, suppliers, regions, or transport modes contribute most to delivery delays?
7. Where is quality leakage occurring through rejected quantities?
8. Which suppliers present greater operational risk or exposure?
9. How does freight cost vary across transport modes and carriers?
10. How does supply chain performance trend over time?
11. Which areas should management prioritize for procurement and logistics improvement?

---

## 📂 Dataset Overview

The project uses operational supply chain data covering procurement, suppliers, shipments, logistics, and monthly targets.

### Core Data Areas

| Data Area | Purpose |
|---|---|
| Purchase Orders | Analyze procurement activity, spend, quantities, pricing, and PO status |
| Supplier Data | Evaluate supplier performance, quality, delivery, and risk |
| Quantity Data | Analyze ordered, received, and rejected quantities |
| Shipment Data | Evaluate delivery dates, promised dates, delays, and transport modes |
| Carrier Data | Compare carrier performance and SLA achievement |
| Warehouse Data | Support logistics and operational analysis |
| Monthly Targets | Compare actual procurement spend with planned targets |

---

## 🧩 Data Model

The Power BI model follows a **Galaxy Schema** approach with two primary fact tables:

### Fact Tables

- **Actual Procurement Fact** — Transaction-level procurement data at PO-line grain.
- **Target Fact** — Monthly procurement targets at category-month grain.

### Conformed Dimensions

- **Date Dimension**
- **Category Dimension**
- Supplier and other descriptive attributes support supplier and logistics analysis.

### Key Modeling Decisions

- Actual procurement data is maintained at **PO-line grain**.
- Monthly targets are maintained separately at **category-month grain**.
- Targets are not merged directly into PO-level transactions to avoid target duplication and inflated totals.
- Conformed dimensions allow consistent filtering across fact tables.
- Delivery-date analysis uses the appropriate date relationship for accurate monthly OTD analysis.
- `USERELATIONSHIP()` is used where an inactive delivery-date relationship is required.

This modeling approach ensures reliable actual-versus-target comparisons and accurate time-based analysis.

---

## 📐 KPI Framework

The dashboard uses a defined KPI framework to measure procurement, supplier, quality, and logistics performance.

| KPI | Business Logic | Purpose |
|---|---|---|
| **Actual Spend** | Actual Unit Price × Ordered Quantity | Measures procurement cost |
| **Total POs** | DISTINCTCOUNT(PO_ID) | Measures procurement order volume |
| **OTD %** | On-Time Delivered ÷ Delivered Shipments | Measures delivery reliability |
| **Avg Lead Time** | Order Date → Actual Delivery Date | Measures procurement speed |
| **Rejection Rate %** | Rejected Qty ÷ Received Qty | Measures quality leakage |
| **PPV %** | (Actual Spend − Contract Spend) ÷ Contract Spend | Measures pricing variance |
| **Freight Cost** | SUM(Freight Cost) | Measures logistics cost |
| **SLA Gap** | Actual OTD % − Carrier SLA Target | Measures carrier performance against commitment |

---

## 🧮 DAX & Time Intelligence

DAX was used extensively to create business-ready KPIs, variance calculations, time intelligence measures, dynamic KPI indicators, and interactive analytical logic.

### Key DAX Techniques Used

- `CALCULATE()`
- `DATEADD()`
- `DATESBETWEEN()`
- `DISTINCTCOUNT()`
- `SUM()`
- `DIVIDE()`
- `VAR`
- `SWITCH()`
- `TRUE()`
- `FORMAT()`
- `UNICHAR()`
- `USERELATIONSHIP()`
- Time intelligence calculations
- MoM variance analysis
- Dynamic KPI text
- Conditional formatting logic

### Month-over-Month Analysis

MoM performance was calculated using the current-period value against the previous-month value.

For example, the Actual Spend MoM calculation follows the structure:

`MoM % = (Current Value − Previous Month Value) ÷ Previous Month Value`

Dynamic MoM indicators were also created using `UNICHAR()` to display directional symbols such as:

- ▲ Positive movement
- ▼ Negative movement
- `-0.00%` for no movement

This provides an intuitive KPI experience directly within the dashboard cards.

---

## 📊 Dashboard Structure

The report consists of **three analytical pages**, each designed around a specific business objective.

### 1️⃣ Overview

The Overview page provides an executive-level summary of supply chain performance.

### Key Analysis

- Actual Procurement Spend vs Target Spend
- Total Purchase Orders
- On-Time Delivery %
- Average Lead Time
- Rejection Rate %
- Purchase Order Status
- Supplier Risk Distribution
- Spend Variance by Product Category
- Delivery Delay Analysis
- Month-over-Month KPI Performance

### Business Purpose

Provides management with a quick understanding of:

**Cost → Orders → Delivery → Quality → Risk → Delay Drivers**

---

### 2️⃣ Supplier & Procurement Performance

This page provides a deeper analysis of supplier and procurement performance.

### Key Analysis

- Supplier Performance
- Supplier Rating
- Quality Score
- Delivery Score
- Supplier Risk
- Supplier Exposure
- Purchase Price Variance
- PPV by Supplier
- Supplier-Level Performance
- Monthly PPV Trends

### Business Purpose

Helps procurement teams identify:

- Strong and weak-performing suppliers
- Pricing inefficiencies
- Supplier risk exposure
- Quality concerns
- Delivery performance gaps
- Opportunities for supplier negotiations and improvement

---

### 3️⃣ Logistics & Delivery Performance

This page focuses on logistics, carrier, transportation, and delivery performance.

### Key Analysis

- Carrier OTD vs SLA
- Freight Cost by Transport Mode
- Transit Time by Carrier
- Monthly OTD Trend
- Delayed Shipment Analysis
- Carrier Performance

### Business Purpose

Helps logistics teams identify:

- Underperforming carriers
- SLA gaps
- Transportation cost pressure
- Long transit times
- Major sources of delivery delays
- Opportunities for logistics optimization

---

## 🔍 Key Dashboard Insights

The analysis generated several actionable findings:

### 💰 Procurement Spend

Actual procurement spend stands at approximately **₹991.94M**, remaining below the target across the analyzed period, indicating overall procurement cost control.

### 🚚 On-Time Delivery

Overall **On-Time Delivery stands at 63.71%**, highlighting a significant opportunity to improve delivery reliability and fulfillment performance.

### 📦 Purchase Orders

The dashboard tracks **480 Purchase Orders**, providing visibility into overall procurement activity and order status.

### 🛡️ Supplier Quality

The overall **Rejection Rate is only 0.82%**, indicating comparatively strong supplier quality performance and limited quantity leakage.

### ⏱️ Lead Time

Average lead time stands at **10.43 days**, highlighting opportunities to further optimize procurement and delivery cycles.

### ⚠️ Supplier Risk

Approximately **73% of suppliers fall within the Medium Risk category**, making proactive supplier risk monitoring an important management priority.

### 📈 Spend Variance

**Office & IT Supplies** show the largest unfavorable spend variance at approximately **₹6.3M**, followed by:

- **Electrical & Electronics — ₹3.9M**
- **Maintenance & Tools — ₹2.5M**
- **Safety Supplies — ₹2.0M**

These categories should be prioritized for deeper pricing and procurement analysis.

### 🚛 Delivery Delays

**Road shipments account for the largest share of delayed shipments**, with approximately:

- **Road — 302 delayed shipments**
- **Rail — 113 delayed shipments**
- **Air — 72 delayed shipments**

This highlights road logistics and carrier performance as key areas for SLA improvement.

---

## 💡 Recommendations

Based on the dashboard findings, the following actions are recommended:

### 1. Strengthen Road Carrier Performance

Prioritize root-cause analysis for road shipment delays and review carrier-level SLA performance. Develop corrective action plans for consistently underperforming carriers.

### 2. Improve On-Time Delivery

Investigate supplier, carrier, region, and transport-mode drivers behind the **63.71% OTD rate** and focus improvement initiatives on the largest sources of delay.

### 3. Control Category-Level Spend Variance

Investigate the high variance in **Office & IT Supplies, Electrical & Electronics, and Maintenance & Tools**, with emphasis on actual price, contract price, purchase volume, and supplier-level drivers.

### 4. Proactively Manage Supplier Risk

Closely monitor the large **Medium-Risk supplier segment** and combine supplier risk with spend exposure, quality, and delivery performance when prioritizing supplier reviews.

### 5. Optimize Lead Time

Identify suppliers, routes, and logistics processes with longer-than-average lead times and evaluate opportunities for sourcing, process, and transportation optimization.

### 6. Maintain Strong Quality Performance

Preserve the low **0.82% rejection rate** through continued supplier quality monitoring and early identification of emerging quality issues.

### 7. Establish Continuous KPI Monitoring

Use the dashboard as a recurring management tool to monitor:

**Spend → PPV → OTD → Lead Time → Rejection Rate → Freight Cost → SLA Performance**

---

## 🔄 Project Workflow

**Raw Operational Data**  
↓  
**Data Understanding & Business Problem Identification**  
↓  
**Data Modeling in Power BI**  
↓  
**Galaxy Schema Development**  
↓  
**DAX Measure Development**  
↓  
**KPI & Time Intelligence Creation**  
↓  
**Interactive Dashboard Development**  
↓  
**Supplier & Procurement Analysis**  
↓  
**Logistics & Delivery Analysis**  
↓  
**Business Insights**  
↓  
**Recommendations & Business Impact**

---

## 🛠️ Tools & Technologies

### Business Intelligence

- **Microsoft Power BI**
- Power Query
- DAX

### Data Analysis

- Data Modeling
- Time Intelligence
- KPI Development
- Variance Analysis
- Supplier Performance Analysis
- Procurement Analytics
- Logistics Analytics

### Visualization & Reporting

- KPI Cards
- Bar Charts
- Donut Charts
- Line Charts
- Matrix
- Decomposition Tree
- Interactive Slicers
- Tooltips
- Conditional Formatting
- Dynamic Text
- Drill-down / Interactive Analysis
- Page Navigation

---

## ⭐ Project Highlights

- Built an end-to-end **Supply Chain Analytics Dashboard using Power BI**.
- Developed a **3-page business intelligence report** covering procurement, suppliers, and logistics.
- Created a **Galaxy Schema data model** with separate procurement and target fact tables.
- Developed business-focused **DAX measures and KPIs** for spend, PO volume, OTD, lead time, rejection rate, PPV, freight cost, and SLA performance.
- Implemented **MoM time-intelligence calculations** using DAX.
- Created dynamic KPI variance indicators using `SWITCH()`, `FORMAT()`, and `UNICHAR()`.
- Implemented appropriate date relationships and `USERELATIONSHIP()` for delivery-date analysis.
- Built actual-versus-target procurement analysis without target duplication.
- Analyzed supplier pricing, quality, delivery performance, risk, and exposure.
- Identified major procurement spend variance drivers.
- Analyzed carrier and transport-mode performance.
- Identified road transportation as the major contributor to delayed shipments.
- Translated analytical findings into **actionable business recommendations**.
- Maintained a strong focus on **business problem-solving, analytical thinking, and decision-ready insights**.

---

## 📁 Repository Structure

    Supply-Chain-Analytics/
    │
    ├── 📂 Datasets/
    │   └── Supply_Chain_Procurement.xlsx
    │
    ├── 📂 Reports/
    │   └── Executive_Summary.pdf
    │   └── Supply Chain Analysis.pdf
    │   └── Supply Chain Analysis.pbix
    │
    ├── 📂 Dashboard/
    │   └── Dashboard.png
    │   └── Dashboard_Preview.mp4
    │
    └── 📄 README.md

---

## 🎯 Business Impact

The dashboard converts fragmented procurement and logistics records into **decision-ready supply chain insights**.

It provides management with a centralized view of:

- Procurement cost control
- Spend variance
- Supplier performance
- Supplier risk
- Quality leakage
- Delivery reliability
- Carrier performance
- Logistics cost
- SLA achievement

The solution enables stakeholders to move from scattered operational checks toward a structured analytical approach for **cost optimization, supplier management, delivery improvement, and logistics performance management**.

---

## 🏁 Conclusion

This **Supply Chain Analytics Dashboard** demonstrates how Power BI and DAX can be used beyond basic visualization to solve practical business problems.

By integrating procurement, supplier, quality, risk, and logistics analysis into a single analytical solution, the project provides a structured foundation for improving **procurement cost control, supplier performance, delivery reliability, quality management, and logistics efficiency**.

The analysis indicates that while procurement spend and supplier quality are comparatively well controlled, significant improvement opportunities exist in **On-Time Delivery, category-level spend variance, lead-time optimization, supplier risk management, and road-carrier performance**.

The project showcases practical Power BI capabilities while maintaining a strong focus on:

**Business Problem → Analytical Solution → Insights → Recommendations → Business Impact**

---

## 👨‍💻 About the Project

**Project Type:** Power BI Portfolio Project  
**Domain:** Supply Chain / Procurement & Logistics Analytics  
**Tool:** Microsoft Power BI  
**Analysis Type:** Business Intelligence & Exploratory Data Analysis  
**Primary Techniques:** DAX, Data Modeling, Time Intelligence, KPI Development, Interactive Visualization

---

## 👨‍💻 About Me

**Sanjay Singh**  
Data Analyst | SQL | Excel | Power BI | Python

I am building a portfolio of practical data analytics projects focused on solving real-world business problems through **data analysis, visualization, business intelligence, and actionable insights**.

This project represents my hands-on experience in using **Power BI, DAX, data modeling, KPI development, and business analysis** to transform operational supply chain data into a decision-ready dashboard.

---

## ⭐ Support the Project

If you found this project useful or interesting:

⭐ **Star this repository**  
🍴 **Fork the repository**  
💼 **Connect with me on LinkedIn**  
📂 **Explore my other Data Analytics projects**

---

## 📬 Let's Connect

**Sanjay Singh**

📧 Email: singhsanjay846@gmail.com  
💼 LinkedIn: www.linkedin.com/in/sanjay-singh-509aa7135  
🐙 GitHub: https://github.com/itssanju1806

I'm always open to connecting with fellow data enthusiasts, analysts, recruiters, and professionals working in the analytics space.

**Thanks for visiting this project! 🚀**
