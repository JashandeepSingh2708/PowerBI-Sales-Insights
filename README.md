# Sales-Report
Power BI Sales Dashboard project involving end-to-end data integration, transformation, modeling, and visualization. Developed a one-page dynamic sales report using DAX measures and Power Query for insights like Total Revenue, Gross Profit, QoQ and MoM growth, top performers, and product-wise revenue split.

# 📊 Power BI Sales Insights Dashboard

This repository showcases a comprehensive and interactive Sales Analytics Dashboard built in Power BI. It analyzes sales data from multiple years across products, geographies, categories, and sales representatives. The solution integrates data transformation (Power Query), data modeling (star schema), and dynamic metrics (DAX) to present actionable business insights via a one-page dashboard.

---

## 🚀 Overview

- **Domain**: Sales Analytics  
- **Years Covered**: 2014 – 2017  
- **Tools Used**: Power BI, DAX, Power Query (M), Excel, CSV  
- **Objective**: Build an end-to-end dashboard for sales performance insights with dynamic visualizations and growth metrics (MoM, QoQ)

---

## 📂 Workflow Breakdown

### 🔹 1. Data Collection

- Sales data (2014–2017): Excel files, imported using folder connector  
- Product data: CSV file  
- Lookup tables (Category, SubCategory, SalesRep, Geography): Excel files

---

### 🔹 2. Data Cleaning & Transformation (Power Query)

- 📁 **Appended** all sales files into a single table using folder import (auto-refresh supported)
- 🧹 **Split `Location`** column into `Country` and `Town`
- 🧽 **Removed “ID - ” prefix** from SalesRepID and SubCategoryID using a reusable M function
- 🔗 Created `GeoKey` column in both `Sales` and `Geography` tables
- 📆 Ensured proper date formats and column data types

---

### 🔹 3. Data Modeling

- Built a **Star Schema**:
  - `Sales` → Fact table  
  - Dimensions: `Product`, `SubCategory`, `Category`, `SalesRep`, `Geography`, `DateMaster`
- Used DAX to create a **Calendar Table** (`DateMaster`)
- Defined correct relationships and cardinality between tables

---

### 🔹 4. DAX Measures

<details>
<summary>📐 Click to view all DAX measures</summary>

```dax
-- Calendar Columns
DateMaster = CALENDAR(FIRSTDATE(Sales[Date]), LASTDATE(Sales[Date]))
Month = MONTH(DateMaster[Date])
Month Name = FORMAT(DateMaster[Date], "MMM")
Month Order = DateMaster[Date].[MonthNo]
Quarter = QUARTER(DateMaster[Date])
Week Day = WEEKDAY(DateMaster[Date])
Week Day Name = FORMAT(DateMaster[Date], "DDD")
Week number = WEEKNUM(DateMaster[Date])
Year = YEAR(DateMaster[Date])

-- Metrics
Total Revenue = Sales[Units] * RELATED(Product[RetailPrice])
Total Cost = Sales[Units] * RELATED(Product[StandardCost])
Gross Profit = Sales[Total Revenue] - Sales[Total Cost]

Tot Profit = SUM(Sales[Gross Profit])
Total Rev = SUM(Sales[Total Revenue])
Prvious Month Profit = CALCULATE([Tot Profit], PREVIOUSMONTH(DateMaster[Date]))
MoM Growth = DIVIDE(([Tot Profit] - [Prvious Month Profit]), [Prvious Month Profit])
Prev qtr = CALCULATE([Total Rev], PREVIOUSQUARTER(DateMaster[Date]))
QOQ growth = DIVIDE(([Total Rev] - [Prev qtr]), [Prev qtr])
```

</details>

---

### 🔹 5. Data Exploration & Insights

- Tracked Total Revenue, Total Cost, and Gross Profit
- Compared performance across time using MoM and QoQ
- Analyzed which Products, Categories, and Sales Reps drive most revenue
- Filtered sales by Country, Year, Month

---

### 🔹 6. Dashboard & Visualizations

| Visual Type        | Usage                                        |
|--------------------|----------------------------------------------|
| KPI Cards          | Total Revenue, Gross Profit, Units           |
| Pie/Donut Charts   | Category & Subcategory share                 |
| Clustered Bar      | Revenue by Product, SubCategory              |
| Waterfall Chart    | Contribution breakdown by Product/Year       |
| Line Chart         | MoM & QoQ growth trend                       |
| Slicers            | Filter by Country, Year, Month               |
| Table/Matrix       | Detailed drill-down data                     |
| Scroll bar         | Applied to bar chart with long product list  |

✅ Months are sorted from Jan–Dec using `Month Order` column  
✅ Filters sync across visuals  
✅ Scroll enabled for overflown bar/line charts (like top N products)

---

### 🔹 7. Exporting Code

#### 🟦 DAX Measures

- Open DAX Studio → Connect to PBIX  
- Run: `EVALUATE SUMMARIZECOLUMNS(...)` to export measures  
- Or copy/paste manually into `All_DAX_Measures.txt`

#### 🟩 Power Query M Code

- Go to Power BI → Transform Data  
- Click `Advanced Editor` → Copy the full script to `PowerQuery_MCode.txt`

---

## 📁 Repository Structure

```
📂 PowerBI-Sales-Insights/
├── 📘 README.md
├── 📊 Sales_Insights_Dashboard.pbix
├── 📄 DAX_Measures_PowerBI.pdf
├── 📄 Sales_Report.png
├── 📄 Product.csv
├── 📄 Sales-20250607T153612Z-1-001.xlsx
├── 📄 Categories.xlsx
├── 📄 SubCategories.xlsx
├── 📄 Geography.xlsx
├── 📄 SalesRep.xlsx
```
---





## 📧 Contact

For queries or collaborations, reach me via [LinkedIn](https://www.linkedin.com/in/jashandeep-singh-98142b283/) or email at [jashansaini2708@gmail.com](mailto:jashansaini2708@gmail.com)

---
