
# Amazon Sales Analytics – Power BI Dashboard (README.md)

## 📌 Overview
This README provides a professional, panel‑ready explanation of the complete **Amazon Sales Analytics BI Solution**, developed using **Microsoft Fabric**, **PySpark Notebooks**, **Lakehouse**, **Semantic Models**, and **Power BI Desktop**.

It summarizes the **end‑to‑end architecture**, **data engineering workflow**, **semantic modeling**, **key metrics**, **visual insights**, and **business outcomes**.

The project follows an enterprise‑grade architecture:
```
Microsoft Fabric → File Storage → Notebook (PySpark) → Lakehouse Tables → Semantic Model → Power BI Desktop → Refresh Pipeline
```

---

# 0. 🔄 End‑to‑End Fabric Workflow

## 📂 0.1 Data Source & File Path
Raw dataset uploaded to:
**Microsoft Fabric → Amazon_WKS Workspace → Files → AmazonSales.xlsx**

This file is the single source of truth for the entire analytical solution.

---

## 🧹 0.2 Data Preparation via Notebook (PySpark)
Using **Notebook1**, the following steps were executed:

### ✔ Data Cleaning
- Removed missing/invalid values
- Standardized number/date formats
- Ensured schema consistency

### ✔ New Calculated Columns Created
- Total Discount
- Discounted Price
- Revenue per Unit
- Category-level flags (for deeper segmentation)

### ✔ Calendar Table Generation
Created using PySpark by extracting **min(order_date)** and **max(order_date)** and generating a full dynamic date range.
This enables all **time‑intelligence DAX** such as YOY, YTD, PY, Rolling 12M.

### ✔ Data Filtering & Business Logic
- Removed invalid transaction rows
- Normalized product category names
- Region and Payment Method cleaned

### ✔ Persisted Output
All processed results stored to Lakehouse as:
```
Amazon_tbl (Fact Table)
DimDate (Calendar Table)
```

---

## 📘 0.3 Semantic Model Creation
A Semantic Model was created in Microsoft Fabric using:
- **Amazon_tbl** (Fact)
- **DimDate** (Date Dimension)

### ⭐ Relationship
```
DimDate[date] (1) → (∞) Amazon_tbl[order_date]
```
This is the backbone for all time‑intelligent measures.

### ⭐ DAX Measures Added
- Total Revenue
- YOY Revenue Growth %
- Average Order Value (AOV)
- Total Orders
- Units Sold
- Units Sold Growth %
- Average Price
- Total Discount Value
- Discount %
- Weighted Rating
- Revenue Rolling 12 Months

These measures are consumed by Power BI Desktop.

---

## 🚀 0.4 Fabric Pipeline Automation
A scheduled Data Pipeline was built:
1. **Notebook1 executes** → data cleaned + refreshed
2. **Semantic Model Refresh** → Power BI receives updated data

This ensures the dashboard stays **fully automated**, **fresh**, and **reliable**.

---

## 🖥️ 0.5 Power BI Desktop Connection
Power BI Desktop connects directly to the **Fabric Semantic Model**, enabling:
- Live, governed data access
- Centralized metrics logic (no duplicated DAX)
- Enterprise semantic layer

Final dashboards were designed in Power BI Desktop using the model.

---

# 1. 📊 Executive Overview – Insights Summary

## ⭐ KPIs Included
- **Total Revenue:** 32.87M
- **YOY Revenue Growth:** 100.54%
- **Average Order Value:** 21.92K
- **Total Orders:** 50K
- **Units Sold Growth:** 100.66%
- **Average Price:** 252.51
- **Average Rating:** 3 Stars

## 🎛 Slicers
- Customer Region
- Payment Method
- Product Category
- Ratings
- Year-Month

## 📈 Visuals & Insights
### ✔ Revenue by Payment Method
Revenue spread evenly (~20% each), indicating **healthy multi‑channel adoption**.

### ✔ Units Sold by Product Category
All categories contribute ~25K units → **balanced product portfolio**.

### ✔ Orders by Customer Region
All regions contribute ~25% → **global customer diversification**.

### ✔ Revenue Trend
Shows consistent daily sales with peaks around 60K → **strong seasonal cycles**.

---

# 2. 📦 Product Performance – Insights Summary

## ⭐ KPIs
- **Total Products:** 4K
- **Total Orders:** 50K
- **Total Units Sold:** 150K
- **PY Units Sold:** 75K
- **Units Sold Growth:** +100.66%
- **Avg Review Count:** 249.33
- **Total Discounted Value:** -1.64T

## 📊 Visuals & Interpretation
### ✔ Orders by Product Category
Beauty performs best; Sports, Home & Kitchen slightly lower.

### ✔ Units Sold by Region
Middle East & North America lead with ~38K each.

### ✔ Revenue vs Orders (Scatter)
Clear positive relationship → **high operational predictability**.

### ✔ Matrix Breakdown
Deep-dive view combining:
- Category
- Region
- Payment Method
- Year

---

# 3. 💡 Key Business Insights

### ✔ Massive Revenue Growth
YOY revenue doubled (+100.54%).

### ✔ Balanced Global Presence
All four regions contribute evenly → **low geographic risk**.

### ✔ Strong Product Diversity
All categories deliver consistent volume → **stable multi‑category demand**.

### ✔ Heavy Discount Dependency
A large discount value indicates **aggressive pricing strategy**.

### ✔ Strong Customer Engagement
High average review count shows **high feedback participation**.

### ✔ Seasonal Demand Predictability
Revenue cycles indicate clear **forecastable patterns**.

---

# 4. 🧠 Why This Dashboard Impresses Interview Panels
- Fully connected **Fabric engineering → BI workflow**
- Clean DAX‑driven **semantic model architecture**
- Automated refresh pipeline
- Executive‑friendly design with strong storytelling
- Deep analytical views across product, region, payment, and time
- Professional readability and enterprise framing

---

# 5. 🎤 How To Present This in Interviews
Use this flow:
1. Start with **data ingestion & Fabric workflow**
2. Explain Notebook‑based transformations
3. Show Semantic Model + relationships
4. Discuss DAX metrics and why they matter
5. Walk through each Power BI page logically
6. Highlight business insights and decision impacts
7. Emphasize automation & governance

This structure demonstrates your **end‑to‑end BI ownership**.

---

# 6. 📘 Final Notes
This README includes:
- Complete architecture flow
- File path and Fabric workflow
- Notebook transformation logic
- Semantic model structure & measures
- Automated pipeline
- Dashboard insights & business outcomes

If you want:
- A **DAX Appendix** section
- A **Data Model Diagram (ERD)**
- A **PDF export**
- A **Technical Architecture Diagram**

Just tell me — I can add it anytime!
