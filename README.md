# 📊 Superstore Sales Dashboard — Power BI

A professional Power BI portfolio project built on the Kaggle Superstore Sales Dataset, demonstrating end-to-end business intelligence skills including data modeling, DAX, and report design.

---

## 🖼️ Dashboard Preview

> *Executive Summary | Product Analysis | Regional Breakdown | Order Detail*

---

## 📁 Project Structure

```
superstore-powerbi/
│
├── Superstore_Sales_Dashboard.pbix   # Main Power BI file
├── data/
│   └── superstore.csv                # Source dataset (Kaggle)
└── README.md
```

---

## 🗃️ Data Model

Star schema with 5 tables:

```
Dim_Customer ──┐
Dim_Product  ──┤
Dim_Location ──┼──► Fact_Sales
Dim_Date     ──┘
```

| Table | Description |
|---|---|
| `Fact_Sales` | Order-level transactions — Sales, Profit, Quantity, Discount |
| `Dim_Customer` | Customer ID, Name, Segment |
| `Dim_Product` | Product ID, Name, Category, Sub-Category |
| `Dim_Location` | Postal Code, City, State, Region, Country |
| `Dim_Date` | Full calendar table — Year, Quarter, Month, Week, Day |

---

## 📐 DAX Measures

| Measure | Description |
|---|---|
| `Total Sales` | `SUM(Fact_Sales[Sales])` |
| `Total Profit` | `SUM(Fact_Sales[Profit])` |
| `Profit Margin %` | `DIVIDE([Total Profit], [Total Sales], 0)` |
| `Total Orders` | `DISTINCTCOUNT(Fact_Sales[Order ID])` |
| `YTD Sales` | Year-to-date sales using `TOTALYTD` |
| `MoM Sales Growth %` | Month-over-month growth using `DATEADD` |

---

## 📄 Report Pages

### 1. Executive Summary
- KPI Cards: Total Sales, Total Profit, Profit Margin %, Total Orders
- Line & Column Chart: Monthly Sales trend with MoM Growth %
- Bar Chart: Sales by Category
- Donut Chart: Sales by Customer Segment
- Year Slicer

### 2. Product Analysis
- Top 10 Products by Sales (Top N filter)
- Matrix: Category > Sub-Category with Sales, Profit, Margin %
- Treemap: Sales by Sub-Category
- Category Slicer (Tile style)

### 3. Regional Breakdown
- Map: Sales by State (bubble size = Sales, color = Profit Margin %)
- Bar Chart: Sales by Region
- Stacked Column Chart: Monthly Sales by Region
- Region Slicer (Tile style)

### 4. Order Detail (Drill-through)
- Accessible by right-clicking any Category in the report
- Table: Order-level detail — Order ID, Date, Customer, Product, Sales, Profit
- Filtered KPI Cards
- Bar Chart: Sales by Sub-Category

---

## 🔒 Row-Level Security (RLS)

Region-based RLS implemented with both static and dynamic roles:

| Role | Filter |
|---|---|
| `West Region` | `[Region] = "West"` |
| `East Region` | `[Region] = "East"` |
| `Central Region` | `[Region] = "Central"` |
| `South Region` | `[Region] = "South"` |
| `Dynamic Region` | `[Region] = USERPRINCIPALNAME()` |

Dynamic role automatically filters data based on the logged-in user's email when published to Power BI Service.

---

## 🛠️ Tools & Skills Used

- **Power BI Desktop** — Report design & publishing
- **Power Query (M)** — Data transformation & star schema modeling
- **DAX** — Measures, time intelligence, dynamic calculations
- **Row-Level Security** — Static & dynamic RLS
- **Data Modeling** — Star schema design

---

## 📦 Dataset

- **Source:** [Superstore Sales Dataset — Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)
- **Rows:** ~10,000 orders
- **Period:** 2014–2018
- **Region:** United States

---

## 👤 Author

**Mahmoud**
Data Analyst | Power BI | SQL | Python

- 📧 [mahmoudsalah.at757@gmail.com]
- 💼 [www.linkedin.com/in/mahmoud-salah-al]
- 🐙 [mahmoudsalahat757-cell]
