# 🏭 DataCo Supply Chain Analytics Project

A full-scale **data analytics and business intelligence project** on the [DataCo Smart Supply Chain dataset](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis).  
This project combines **SQL, Python (Pandas, Seaborn, Matplotlib)**, and **statistical methods (ANOVA & T-Test)** to extract actionable insights about **sales, customers, delivery efficiency, and business performance**.

---

## 🎯 Objective

To perform a **comprehensive data-driven analysis** of supply chain operations and answer key business questions:
- What are the top-performing products, categories, and departments?  
- How efficient are shipping modes and delivery timelines?  
- Which customers and segments drive the most revenue?  
- What is the repeat purchase behavior among customers?  
- Are there statistically significant differences between shipping modes?

---

## 🧠 Project Overview

| Component | Description |
|------------|--------------|
| **Dataset** | DataCo Supply Chain for Big Data Analysis (180K+ rows, 52 columns) |
| **Tech Stack** | Python, SQLite, Pandas, Seaborn, Matplotlib, SciPy |
| **Goal** | Supply chain optimization & operational performance insights |
| **Environment** | Google Colab / Jupyter Notebook |

---

## 🧱 Workflow Summary

### 1️⃣ Data Cleaning & Setup
- Removed fully null columns: `Order Zipcode`, `Product Description`
- Dropped remaining missing values
- Verified duplicates:
  - `Customer Id` → Duplicates exist (multiple orders)
  - `Order Id` → Duplicates exist (multi-item orders)
  - `Order Item Id` → ✅ Unique
- Created SQLite database: `supply_chain.db`
- Imported data table for SQL querying and aggregation

---

### 2️⃣ Exploratory SQL Analysis

#### 🔹 Monthly Sales Trend
```sql
SELECT strftime('%Y-%m', "order date (DateOrders)") AS year_month, SUM("Sales") AS total_sales
FROM supply_chain
GROUP BY year_month
ORDER BY year_month;
```
📈 **Insight:** Strong monthly growth with seasonal fluctuations.

#### 🔹 Top Revenue Products
- `Field & Stream Sportsman 16 Gun Fire Safe` → $6.22M highest revenue  
📊 **Visualization:** Bar chart (Top 10 products by revenue)

#### 🔹 Top Departments by Profit
| Department | Avg Profit | Comment |
|-------------|-------------|----------|
| Technology | Highest | Strong performance |
| Outdoors | Mid | Good profit margins |
| Furniture | Moderate | Consistent performer |

#### 🔹 Country-wise Sales
| Country | Total Sales |
|----------|--------------|
| USA (EE. UU.) | Highest |
| Canada | Second |
| Mexico | Moderate |

---

### 3️⃣ Shipping Performance & Delivery Efficiency

#### Average Delivery Days by Shipping Mode
| Shipping Mode | Avg Days (Real) | Orders | Insight |
|----------------|-----------------|----------|----------|
| First Class | 2 | Low volume | Fastest |
| Second Class | 3 | Moderate | Efficient |
| Standard Class | 4 | Most | Slower but stable |

#### Delay Percentage Analysis
| Shipping Mode | Delay % | Comment |
|----------------|----------|----------|
| First Class | 100% | Small sample, always late |
| Second Class | 63% | Moderate delay |
| Standard Class | 39.77% | Lowest delay |

📦 **Insight:** Standard Class dominates in order count but has moderate delays.

---

### 4️⃣ Customer Analysis

#### Customer Segmentation
| Segment | Customers | Total Sales | Avg Sales |
|----------|------------|--------------|------------|
| Consumer | 10,692 | $19.09M | Highest contributor |
| Corporate | 6,234 | $11.16M | Consistent segment |
| Home Office | 3,715 | $6.51M | Smaller share |

📊 **Insight:** Consumer segment drives over **50% of total revenue**.

#### Top Customers
- Customer ID **791** generated the highest sales volume.
- Customer ID **5004** purchased the highest total item quantity.

---

### 5️⃣ Order Status Distribution
| Status | Orders | Comment |
|---------|----------|----------|
| Completed | 59,487 | ✅ Most successful |
| Pending | 20,224 | ⚠️ Needs attention |
| On Hold | 9,803 | 🔄 Process bottleneck |
| Payment Review | 1,893 | ⚠️ Financial verification delays |

📊 **Insight:** ~35% of orders are pending or under review — indicates possible process inefficiencies.

---

### 6️⃣ Product & Category Insights
- **Fishing**, **Camping**, and **Hunting** are the top categories.
- These categories represent the majority of total order value.

📈 **Visualization:** Bar chart of top 10 categories by order value.

---

### 7️⃣ Geographical Distribution
- Major order density around **(Longitude: -100, Latitude: 40)** — Central U.S.
📍 **Visualization:** Scatterplot (Longitude vs Latitude, colored by Sales)

---

### 8️⃣ Customer Retention & Repeat Purchases

#### Repeat Rate Analysis
```sql
SELECT
  SUM(CASE WHEN n_orders > 1 THEN 1 ELSE 0 END) * 100 / COUNT(*) AS repeat_rate_percentage
FROM (
  SELECT COUNT(DISTINCT "Order Id") AS n_orders
  FROM supply_chain
  GROUP BY "Customer Id"
);
```
| Metric | Value |
|---------|--------|
| Repeat Purchase Rate | **57%** |
| Total Customers | 20,641 |
| Repeat Customers | 11,768 |

📊 **Insight:** More than half of the customers reorder, indicating strong retention.

#### Time to Second Purchase
- **Median:** 207.0 days
- **Average:** 248.8 days


### 9️⃣ Profit Margins vs Order Volume
- As **order volume increases**, **profit margin** rises proportionally.  
- Outliers removed using IQR filtering for clarity.

📈 Scatterplot: Order Volume vs Profit → Positive correlation.

---

### 🔬 Statistical Analysis

#### ANOVA Test (Shipping Modes)
- **Goal:** Determine if shipping modes have different delivery times.  
- **Result:**  
  - F-statistic = significant  
  - p-value < 0.05 → ✅ Statistically significant differences exist.

#### Pairwise T-Tests
| Comparison | Mean Diff (Days) | Significance |
|-------------|-----------------|---------------|
| Standard Class vs Second Class | Non Significant | ns |
| Others | are highy significant | *** |

📊 **Insight:** Delivery efficiency varies notably between modes.

---

## 🧾 Key Performance Indicators (KPIs)

| KPI | Value | Insight |
|------|--------|----------|
| Total Orders | 6,537,937,304.00 |  |
| Total Sales | $36,781,302.12|  |
| Avg Profit per Order |  $21.97|  |
| Repeat Purchase Rate | 57% | Strong retention |
| Avg Delivery Delay | 3.5 days | Operational improvement area |

---

## 💡 Business Insights & Recommendations

| Area | Observation | Recommendation |
|-------|--------------|----------------|
| Shipping | Standard Class is reliable but slower | Optimize logistics to reduce average delay |
| Customer Behavior | High repeat rate | Launch loyalty programs to increase retention |
| Order Management | non-completed orders | Investigate reasons for "Pending" status |
| Profitability | Tech & Fishing products most profitable | Increase stock and marketing in these categories |
| Market | U.S. central region dominates | Focus promotions in high-demand zones |

---

## 🧾 Project Evaluation (Industry Standard)

| Evaluation Aspect | Rating (out of 10) | Comment |
|--------------------|--------------------|----------|
| **Data Cleaning & Transformation** | Efficiently managed large dataset |
| **SQL & Database Integration** | Excellent analytical SQL usage |
| **Visualization & Storytelling** | Insightful & business-focused visuals |
| **Statistical Analysis** | Strong addition of ANOVA & T-tests |


---

## 🚀 How to Run

1. Download dataset: `DataCoSupplyChainDataset.csv`  
2. Open `supply_chain_analysis.py` in **Colab** or **Jupyter**  
3. Run sequentially (no manual steps needed)  
4. Outputs:
   - SQLite database (`supply_chain.db`)
   - Charts (auto-rendered inline)
   - Executive Summary printed in console

---

## 📊 Visual Highlights
- Monthly Sales Trend  
- Top 10 Products by Revenue  
- Shipping Delay by Mode  
- Customer Retention Distribution  
- Profit vs Order Volume  
- Geographical Order Distribution  


---

## 🧠 Future Enhancements
- Predict **delivery delays** using Machine Learning  
- Build **interactive dashboard (Power BI / Tableau)**  
- Perform **regional sales forecasting**

---

## 👤 Author

**Sourav Mondal**  
Business Analytics | SQL | Python | Data Visualization  
📍 DataCo Supply Chain Analytics (4/11/2025)

**Connect:**    
📧 souravmondal5f@gamail.com  

---
