# Vendor Performance & Strategic Analytics

> An end-to-end vendor performance and procurement analytics project that combines Python, SQL, and Power BI to identify profitability drivers, procurement opportunities, inventory risks, and vendor concentration.

---

## 📌 Project Overview

This project analyzes vendor, purchase, sales, pricing, freight, and inventory-related data to evaluate vendor performance and support procurement decisions.

The project builds a consolidated **Vendor Sales Summary** from multiple transactional tables, performs exploratory and statistical analysis in Python, and presents the results through an interactive Power BI dashboard.

The analysis focuses on:

- Vendor profitability and sales performance
- Procurement and bulk-purchasing efficiency
- Vendor concentration and dependency
- Inventory turnover and unsold capital
- High-margin, low-volume growth opportunities

The underlying raw data contains approximately **1.8 GB** of transactional data, including **12.8 million sales records** and **2.3 million purchase records**. The final analytical dataset contains **10,692 vendor-brand records**.

---

## 🎯 Business Problem

A business managing a large vendor and product portfolio needs to understand which vendors drive revenue, which vendors generate stronger margins, where inventory is becoming stagnant, and how procurement decisions affect costs.

The analysis addresses questions such as:

- Which vendors and brands contribute the most sales?
- Are high-volume vendors also the most profitable?
- How does order size affect purchase price?
- How dependent is the business on its largest vendors?
- Which vendors have critically low inventory turnover?
- Where is capital tied up in unsold inventory?
- Which high-margin, low-volume brands could be targeted for growth?

The objective is to convert large-scale transactional data into actionable insights for procurement, inventory, pricing, and vendor-management decisions.

---

## 🔍 Key Objectives

- Evaluate vendor sales and profitability performance
- Identify the top-performing vendors and brands
- Analyze the relationship between order volume and purchase price
- Identify high-margin, low-volume "Hidden Gem" brands
- Measure vendor concentration using Pareto analysis
- Identify vendors with low inventory turnover
- Quantify unsold inventory value
- Compare profit margins between high-volume and low-volume vendors
- Validate business findings using statistical testing
- Build a consolidated Power BI dashboard for decision-making

---

## 📊 Dataset

**Source:** Project CSV datasets included in the repository

**Raw Data Size:** Approximately 1.8 GB

**Raw Transaction Volume:**
- 12.8 million sales records
- 2.3 million purchase records

**Final Analytical Dataset:** 10,692 vendor-brand records

### Main Data Tables

| Table | Description |
|---|---|
| `purchases` | Purchase transactions including vendor, brand, quantity, purchase price, and purchase dollars |
| `purchase_prices` | Vendor/product pricing information including purchase price, actual price, and volume |
| `vendor_invoice` | Vendor invoice information including freight costs |
| `sales` | Sales transactions including brand, quantity, selling price, sales dollars, and excise tax |
| `vendor_sales_summary` | Consolidated vendor-brand analytical dataset created from the source tables |

### Main Analytical Features

| Feature | Description |
|---|---|
| `VendorNumber` | Unique vendor identifier |
| `VendorName` | Vendor name |
| `Brand` | Brand identifier |
| `PurchasePrice` | Vendor purchase price |
| `ActualPrice` | Actual product price |
| `Volume` | Product/order volume |
| `TotalPurchaseQuantity` | Total quantity purchased |
| `TotalPurchaseDollars` | Total purchase value |
| `TotalSalesQuantity` | Total quantity sold |
| `TotalSalesDollars` | Total sales value |
| `FreightCost` | Total freight cost associated with the vendor |
| `GrossProfit` | Sales value minus purchase value |
| `ProfitMargin` | Gross profit as a percentage of sales |
| `StockTurnover` | Sales quantity relative to purchase quantity |
| `SalesToPurchaseRatio` | Sales value relative to purchase value |

---

## 🛠️ Tools & Technologies

- **Python** — Data ingestion, data cleaning, exploratory data analysis, feature engineering, and statistical analysis
- **Pandas** — Data manipulation and transformation
- **SQLite** — Storage and querying of large transactional datasets
- **SQL** — Joins, aggregations, CTEs, and creation of the consolidated vendor summary
- **Power BI** — Interactive dashboard and business visualization
- **Jupyter Notebook** — Exploratory data analysis and analytical workflow
- **Logging** — Tracking data ingestion and vendor-summary pipeline execution

---

## 📈 Analysis

### 1. Vendor & Brand Performance

The analysis evaluates vendor and brand performance using sales, purchase value, gross profit, and profit margin.

**Key questions:**

- Which vendors generate the most sales?
- Which brands contribute the most revenue?
- How do high-volume vendors compare with smaller vendors?
- Which vendors and brands are important for overall cash flow?

**Methods used:**

- SQL aggregation
- Vendor/brand segmentation
- Ranking
- Revenue and profitability analysis

### 2. Procurement & Pricing Optimization

Order sizes were segmented into Small, Medium, and Large categories to investigate the relationship between order volume and unit purchase price.

**Key finding:**

Moving from Small to Large order volumes was associated with an approximately **73% reduction in unit purchase price**.

The analysis found a strong inverse relationship between order size and purchase price, indicating significant economies of scale from larger orders.

### 3. Vendor Concentration & Dependency

A Pareto analysis was performed to understand how procurement value is distributed across vendors.

**Key finding:**

The **Top 10 vendors account for 65.35% of total procurement value**, creating both purchasing efficiency and supplier concentration risk.

### 4. Inventory Velocity & Capital Health

Vendor-level stock turnover and unsold inventory value were analyzed to identify stagnant inventory and capital tied up in unsold products.

Examples of critically low stock turnover include:

- **TRUETT HURST:** 0.0417
- **IRA GOLDMAN AND WILLIAMS, LLP:** 0.0750
- **UNCORKED:** 0.2172

The vendors with the highest unsold inventory value include:

- **DIAGEO NORTH AMERICA INC:** $980.08K
- **MARTIGNETTI COMPANIES:** $872.08K
- **JIM BEAM BRANDS COMPANY:** $810.30K

### 5. High-Margin, Low-Volume "Hidden Gems"

Brands were screened using:

- **High Margin Threshold:** 38%
- **Low Sales Threshold:** $300

These brands represent potential growth opportunities where additional marketing, retail placement, or pricing attention could increase profitability.

### 6. Statistical Validation

The project uses confidence intervals and an independent two-sample t-test to compare profit margins between high-volume and low-volume vendor groups.

**Groups:**

- Top Vendors: Top 25% based on `TotalSalesDollars`
- Low Vendors: Bottom 25% based on `TotalSalesDollars`

**Results:**

| Group | Mean Profit Margin | 95% CI |
|---|---:|---:|
| Top Vendors | 31.86% | 31.57% – 32.15% |
| Low Vendors | 33.01% | 32.77% – 33.26% |

**T-Statistic:** -5.9978

**P-Value:** 0.0000

**Verdict:** Reject H0

The statistical test provides strong evidence that the difference in mean profit margins between the two vendor groups is statistically significant.

---

## 📊 Dashboard / Visualizations

The Power BI dashboard provides a consolidated view of vendor sales, procurement, profitability, vendor contribution, brand performance, and inventory risk.

### Dashboard Preview

![Vendor Performance Dashboard](Power%20BI/Dashboard.png)

### Main KPIs

- **Total Sales:** $450.02M
- **Total Purchase:** $319.63M
- **Gross Profit:** $138.74M
- **Profit Margin:** 32.27%
- **Unsold Capital:** $8.35M

### Dashboard Components

- Purchase contribution by vendor
- Top vendors by sales
- Top brands by sales
- Low-performing vendors
- Low-performing brands
- Sales vs. profit margin analysis
- Vendor concentration analysis

---

## 💼 Business Recommendations

Based on the analysis, the following actions are recommended:

1. **Consolidate fragmented purchase orders.**  
   Shift procurement toward larger order volumes where operationally feasible to capture the identified bulk-pricing advantage and reduce margin erosion.

2. **Maintain strategic relationships with major vendors while reducing dependency risk.**  
   Top vendors provide critical sales volume and cash flow, but the 65.35% procurement concentration means alternative suppliers should be evaluated where practical.

3. **Develop high-margin, low-volume "Hidden Gem" brands.**  
   Increase marketing exposure, retail placement, or pricing attention for brands meeting the high-margin and low-sales criteria.

4. **Monitor stagnant inventory.**  
   Prioritize vendors with critically low stock turnover and high unsold inventory value to reduce tied-up working capital.

5. **Balance volume and profitability in vendor strategy.**  
   High-volume vendors should continue supporting core revenue, while smaller high-margin vendors can be developed to improve overall profitability.

---

## 📁 Project Structure

```text
Vendor-Performance-Data-Analysis/
│
├── README.md
│
├── Database/
│   └── inventory.db
│
├── Datasets/
│   ├── begin_inventory.csv
│   ├── end_inventory.csv
│   ├── purchase_prices.csv
│   ├── purchases.csv
│   ├── sales.csv
│   ├── vendor_invoice.csv
│   └── vendor_sales_summary.csv
│
├── logs/
│   ├── ingestion_db.log
│   └── get_vendor_summary.log
│
├── Power BI/
│   ├── Dashboard.png
│   └── vendor_Performance_Dashboard.pbix
│
├── Python/
│   ├── Exploratory Data Analysis.ipynb
│   ├── get_vendor_summary.py
│   ├── ingestion_db.py
│   └── Vendor Performance Analysis.ipynb
│
└── Report/
    └── Vendor_Performance_Strategic_Analytics_Report.pdf
```



---

## 📂 Project Files

| File / Folder | Description |
|---|---|
| `Database/inventory.db` | SQLite database containing the ingested datasets |
| `Datasets/` | Raw and processed CSV datasets |
| `Python/ingestion_db.py` | Database ingestion pipeline |
| `Python/get_vendor_summary.py` | Vendor summary creation and data-cleaning pipeline |
| `Python/Exploratory Data Analysis.ipynb` | Exploratory data analysis and analytical workflow |
| `Power BI/Dashboard.png` | Preview of the Power BI dashboard |
| `Power BI/` | Power BI dashboard file |
| `Report/` | Detailed strategic analytics report |
| `logs/` | Pipeline execution logs |

---

## 📄 Detailed Report

A detailed project report containing the methodology, statistical analysis, visualizations, business findings, and strategic recommendations is available in the [Report](https://github.com/rijvanpinjari/Vendor-Performance-Analysis/tree/main/Report) folder.
