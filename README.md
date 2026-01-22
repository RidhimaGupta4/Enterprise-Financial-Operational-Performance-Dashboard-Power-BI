# 📊 Enterprise Financial & Operational Performance Dashboard — Power BI

A **Power BI** project designed to provide executives, managers, and analysts with a consolidated view of enterprise financial and operational KPIs. The dashboard integrates multiple business domains—finance, sales, operations, inventory, and customers—into an interactive reporting solution for data-driven decision-making.

---

## 🚨 Problem Statement

Enterprises often struggle with **disconnected financial, operational, and customer data**, leading to:

- Limited visibility into **overall business performance**  
- Difficulty tracking key metrics like revenue, profit, gross margin, and operational efficiency  
- Challenges in identifying trends and performance gaps across regions, products, and customers  
- Inefficient decision-making due to siloed datasets and manual reporting  

**This project addresses these challenges by consolidating data into a single, interactive dashboard for real-time insights.**

---

## ✅ Solution

The dashboard delivers a **centralized analytics platform** that:

- Tracks **financial KPIs**: Revenue, Gross Profit, Gross Margin %  
- Monitors **operational performance**: On-Time Delivery %, Inventory Stock-out Days, Supplier OTIF  
- Provides **customer insights**: Top customers, retention, churn, segment-level sales trends  
- Uses **interactive filters and slicers** for flexible drill-down by date, region, product, and customer  
- Supports executives and managers with **data-driven decision-making**  
- Skips Drillthrough & Tooltip polish in this version, but still allows exploration through slicers and tabs  

---

## 🚀 Project Workflow

### 🟦 1. Data Preparation
- Collected datasets from multiple enterprise domains: finance, sales, operations, inventory, and customer data  
- Ensured clean column names and correct data types  
- Created sample CSVs for testing or connected directly to enterprise sources  

---

### 🟩 2. Data Load
- Imported all datasets into **Power BI Desktop**  
- Verified and corrected data types:
  - IDs → Whole Number  
  - Dates → Date  
  - Currency/Decimal fields → Currency/Decimal  

---

### 🟨 3. Data Modeling
Built a **Star Schema**:

**Dimension Tables:**

- `dim_date` → Calendar table for time-based analysis  
- `dim_customer` → Customer profiles and segmentation  
- `dim_product` → Product categories and details  

**Fact Tables:**

- `fact_sales` → Revenue, Profit, Margin, Units Sold  
- `fact_orders` → Order records, promised vs. delivery dates  
- `fact_inventory` → Inventory levels, stock-out days, supplier performance  

**Relationships:**

- `dim_date[Date]` → `fact_sales[Date]`  
- `dim_customer[CustomerID]` → `fact_sales[CustomerID]`  
- `dim_product[ProductID]` → `fact_sales[ProductID]`  

---

### 🟧 4. DAX Measures (Core KPIs)
- **Total Revenue** → `SUM(fact_sales[Revenue])`  
- **Gross Profit** → `SUM(fact_sales[Profit])`  
- **Gross Margin %** → `DIVIDE([Gross Profit], [Total Revenue], 0)`  
- **On-Time Delivery %** → `DIVIDE(COUNTROWS(FILTER(fact_orders, fact_orders[DeliveredOnTime]=TRUE)), COUNTROWS(fact_orders), 0)`  
- **Inventory Stock-out Days** → `AVERAGE(fact_inventory[StockOutDays])`  
- **Supplier OTIF %** → `DIVIDE(COUNTROWS(FILTER(fact_inventory, fact_inventory[OnTimeDelivery]=TRUE)), COUNTROWS(fact_inventory), 0)`  
- **Top Customers by Revenue** → `SUM(fact_sales[Revenue])` with customer filter  

---

### 🟥 5. Dashboard Pages

 [Executive Summary Page](https://github.com/Hassan0397/Enterprise-Financial-Operational-Performance-Dashboard-Power-BI/blob/main/Executive%20Summary.png)

- KPI Cards: Revenue, Gross Profit, Gross Margin %, On-Time Delivery %  
- Trend Analysis: Revenue and KPI comparisons over time  

 [Finance Deep Dive Page](https://github.com/Hassan0397/Enterprise-Financial-Operational-Performance-Dashboard-Power-BI/blob/main/Finance-Deep%20Dive.png)

- Revenue & Gross Profit by Product Category  
- Profitability trends over time  
- Region-wise financial performance  

 [Operations Deep Dive Page](https://github.com/Hassan0397/Enterprise-Financial-Operational-Performance-Dashboard-Power-BI/blob/main/Supply%20details.png)

- On-Time Delivery % by region & product  
- Inventory Stock-out Days  
- Supplier On-Time Delivery %
  

**Interactive Filters & Slicers:**

- Date (Year, Month, Quarter)  
- Region & Product filters  
- Customer segmentation  

---

## 🛠 Setup Instructions

1. Open **Power BI Desktop**  
2. Load the provided datasets or connect to enterprise data sources  
3. Apply Power Query transformations (if any)  
4. Build relationships as defined in the Data Model section  
5. Add the DAX measures for KPIs  
6. Format visuals, apply themes, and configure interactive slicers  

---

## ✅ Key Features Implemented

- Core KPI dashboards: Executive, Finance, Operations, Customer  
- Interactive slicers and filters for flexible analysis  
- Professional formatting of all measures, tables, and matrix visuals  
- Trend analysis for financial and operational metrics  

---
