# 🧩 Project 1 — Power BI Sales Performance Dashboard

> **Report:** `Project 1.pbix`  
> **Type:** Interactive Power BI Dashboard  
> **Scope:** Revenue • Orders • Profit • Returns • Customers (2020–2022)

---

## 📊 Overview
**Project 1** is a Power BI report that consolidates sales and customer data across regions to provide leadership and analysts with an at-a-glance view of business performance. It highlights revenue trends, order volumes, profit vs. targets, product performance, and customer behavior.

**Audience:** Operations, Finance, Leadership  
**Update Cadence:** Daily (configurable)  
**Distribution:** Power BI Service + SharePoint embed

---

## 🔑 Key Metrics (examples)
- **Total Revenue:** _e.g.,_ `$XX.XM`
- **Total Orders:** _e.g.,_ `XX.XK`
- **Total Profit:** _e.g.,_ `$XX.XM`
- **Return Rate:** _e.g.,_ `X.X%`
- **Unique Customers:** _e.g.,_ `XX.XK`
- **Revenue / Customer:** _e.g.,_ `$X,XXX`

> Replace with your actual KPI values after refresh.

---

## 🧭 Report Pages
1. **Executive Overview** — Core KPIs, revenue trend, MoM deltas  
2. **Product Analysis** — Orders/returns by category, top products  
3. **Profit & Targets** — Revenue/profit vs. target with variance  
4. **Customer Insights** — Demographics, income/occupation segments  
5. **Regional View** — Azure Maps by continent/market  
6. **Top Customers** — Ranked table: orders and revenue

---

## 🧮 Data Model & Sources
- **Fact:** Orders/Sales (Revenue, Profit, Returns, Quantities, Dates)
- **Dimensions:** Products, Customers, Categories, Geography, Date
- **Connectivity:** Import or DirectQuery to your warehouse (e.g., Snowflake / SQL / Azure Synapse)
- **Geo:** Azure Maps visual for regional analysis

### Example DAX
```DAX
-- Return Rate
Return Rate :=
DIVIDE( SUM(Fact[ReturnedQty]), SUM(Fact[OrderQty]) )

-- Profit Margin %
Profit Margin % :=
DIVIDE( SUM(Fact[Profit]), SUM(Fact[Revenue]) )

-- MoM Revenue %
MoM Revenue % :=
VAR Prev = [Previous Month Revenue]
RETURN DIVIDE([Current Month Revenue] - Prev, Prev)
# Sales-Report-by-Power-BI
