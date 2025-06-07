# Sales-Report
Power BI Sales Dashboard project involving end-to-end data integration, transformation, modeling, and visualization. Developed a one-page dynamic sales report using DAX measures and Power Query for insights like Total Revenue, Gross Profit, QoQ and MoM growth, top performers, and product-wise revenue split.

# 📊 Power BI Sales Insights Dashboard

This Power BI project presents a comprehensive sales dashboard that offers insights into performance across multiple years and geographies. It demonstrates key aspects of a full business intelligence pipeline including data transformation, modeling, DAX calculations, and compelling visual storytelling.

---

## 🚀 Project Overview

**Goal**: To build a dynamic and responsive Power BI dashboard that summarizes sales data, identifies top products and sales reps, and evaluates quarter-over-quarter and month-over-month performance metrics.

---

## 📂 Data Sources

- `Sales` data (Yearly Excel/CSV files for 2014-2017)
- `Categories` (Excel)
- `SubCategories` (Excel)
- `Geography` (Excel)
- `Product` (CSV)
- `SalesRep` (Excel)

---

## 🔧 Steps Followed

### 1. 📥 Data Collection
- Imported datasets from Excel and CSV files.
- Combined yearly sales data (2014–2017) using **Power Query** with a **folder-based approach** for automatic updates.

### 2. 🧹 Data Cleaning & Transformation
- Split the `Location` column into `Country` and `City`.
- Created a unique `GeoKey` in both `Sales` and `Geography` tables.
- Cleaned `SalesRepID` and `SubCategoryKey` by removing prefix using a reusable Power Query function.

### 3. 🧠 Data Modeling
- Created a **Date table** using DAX: `CALENDAR(FIRSTDATE(), LASTDATE())`.
- Built relationships between:
  - Sales ↔ Product
  - Sales ↔ DateMaster
  - Sales ↔ Geography
  - Sales ↔ SalesRep
  - Product ↔ SubCategory ↔ Category

### 4. 📊 DAX Calculations

| Measure | Formula |
|--------|---------|
| Total Revenue | `Sales[Units] * RELATED(Product[RetailPrice])` |
| Total Cost | `Sales[Units] * RELATED(Product[StandardCost])` |
| Gross Profit | `Sales[Total Revenue] - Sales[Total Cost]` |
| MoM Growth | `([Tot Profit] - [Previous Month Profit]) / [Previous Month Profit]` |
| QoQ Growth | `([Total Rev] - [Prev qtr]) / [Prev qtr]` |
| AVG Sales/Day | `AVERAGEX(VALUES(Sales[Date]), [Total Rev])` |

➡️ [Full list of DAX Measures (PDF)](./DAX_Measures_PowerBI.pdf)

---

## 📈 Visualizations Used

<details>
<summary>Click to Expand Visualization List</summary>

- 📌 **Total Revenue / Gross Profit / Units Sold Cards**
- 📊 **Stacked Column Chart** for Revenue by Product and Subcategory
- 🥧 **Pie Chart** for Sub Category Share
- 💼 **Top 5 Sales Reps** as a bar list
- 🟠 **Donut Chart** for Revenue by Category
- 📆 **Waterfall Chart** for Revenue by Year & Product
- 📈 **Line Chart** for:
  - QoQ Revenue Growth
  - MoM Gross Profit Growth
</details>

---

## 🖥️ Dashboard Features

- Filter by Country, Year, and Month.
- Dynamic calculations using DAX.
- Handles new/removed files automatically via folder-based Power Query.
- Responsive to slicers and time filters.
- Scrollable visual.

---

## 🛠️ How to Create Power BI M Code and DAX Measure Files

1. **DAX Measures**: Go to **Modeling > New Measure**, copy-paste the formula.
2. **M Code (Power Query)**:
   - Use **Advanced Editor** in Power Query to extract M code.
   - File > Advanced Editor > Copy entire query logic.
   - Save as `.txt` or `.m` file for documentation.
3. You can also export M queries by:
   - Right-click query > **Properties** > Copy code or export steps manually.

---

## 📎 Project Status

✅ Completed and tested  
📤 Published to GitHub with documentation  
📅 Can be enhanced by including drill-through reports or R/Python visuals in future

---

## 📧 Contact

For queries or collaborations, reach me via [LinkedIn](https://www.linkedin.com/in/jashandeep-singh-98142b283/) or email at [jashansaini2708@gmail.com](mailto:jashansaini2708@gmail.com)

---
