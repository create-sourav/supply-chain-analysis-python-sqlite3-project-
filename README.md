# 📊 Supply Chain Analysis Project

A comprehensive analysis of supply chain data using Python, SQL, and data visualization libraries to extract actionable business insights.

## 🎯 Overview

This project analyzes supply chain operations data to identify trends, optimize logistics, and understand customer behavior. The analysis covers sales patterns, product performance, shipping efficiency, customer segmentation, and geographical distribution of orders.

## 🛠️ Technologies Used

- **Python 3.x**
- **pandas** - Data manipulation and analysis
- **matplotlib** - Data visualization
- **seaborn** - Statistical data visualization
- **sqlite3** - Database management
- **Google Colab** - Development environment

## 📁 Dataset

The analysis uses the DataCo Supply Chain Dataset (`DataCoSupplyChainDataset.csv`) with the following preprocessing steps:

- ❌ Removed columns: `Order Zipcode`, `Product Description`
- 🧹 Dropped rows with null values
- 💾 Created SQLite database for efficient querying
- 🔑 Identified unique identifiers: `Order Item Id` (no duplicates), while `Customer Id` and `Order Id` contain duplicates due to repeat customers and multiple items per order

## 🔍 Key Findings

### 💰 Sales Performance
- **Monthly Sales Trend**: Analyzed temporal patterns in sales data to identify seasonal trends and growth patterns
- **Top Revenue Generator**: Field & Stream Sportsman 16 Gun Fire Safe leads with **$6.23M** in revenue

### 📦 Product & Department Analysis
- **Top 10 Products**: Identified highest revenue-generating products
- **Best Department**: Technology department shows the highest average profit per order
- **Top Category**: Fishing category leads in total order item value

### 👥 Customer Insights
- **Primary Segment**: Consumer segment contributes the highest total sales
- **Top Customer**: Customer ID 791 generates the highest total sales
- **Top 10 Customers**: Analyzed by total sales and number of orders

### 🌍 Geographical Distribution
- **Top Markets**: United States (EE. UU.) and Puerto Rico lead in total sales
- **Order Concentration**: Majority of orders originate from coordinates around longitude -100, latitude 40 (central United States)

### 🚚 Shipping Performance
- **Standard Class**: Most popular shipping mode but takes ~4 days on average
- **First Class**: Faster delivery at ~2 days shipping time
- Average shipping days analyzed by mode with order volume metrics

### 📋 Order Status
| Status | Count |
|--------|-------|
| ✅ Completed | 59,487 |
| ⏳ Pending | 20,224 |
| ⏸️ On Hold | 9,803 |
| 💳 Payment Review | 1,893 |

## 📊 Analysis Components

### 1️⃣ Data Preprocessing
```python
# Loaded dataset with latin-1 encoding
# Handled missing values
# Removed unnecessary columns
# Checked for duplicates
```

### 2️⃣ Database Creation
```python
# Created SQLite database (supply_chain.db)
# Imported DataFrame to SQL table
# Enabled efficient SQL querying
```

### 3️⃣ Time Series Analysis
- Converted order dates to datetime format
- Grouped sales by month
- Visualized monthly sales trends

### 4️⃣ Revenue Analysis
- Top 10 products by revenue
- Department profitability analysis
- Category performance metrics

### 5️⃣ Customer Analysis
- Customer segmentation by sales
- Top customer identification
- Order frequency patterns

### 6️⃣ Logistics Analysis
- Shipping mode efficiency
- Average delivery times
- Order value by shipping method

### 7️⃣ Geographic Analysis
- Sales by country
- Coordinate-based order distribution
- Geographic visualization using latitude/longitude data

## 🎨 Visualizations

The project includes multiple visualization types:
- **Line plots**: Monthly sales trends
- **Bar plots**: Product revenue, department profits, customer segments
- **Scatter plots**: Geographic distribution of orders
- **Color palettes used**: `viridis`, `plasma`, `magma`, `inferno` for enhanced readability

## 🔎 SQL Queries

The analysis leverages SQL for efficient data aggregation:
- Group by operations for categorical analysis
- Aggregation functions (`SUM`, `AVG`, `COUNT`)
- Sorting and limiting for top-N analysis
- Filtering for data quality

## 🚀 How to Use

1. 📤 Upload the DataCo Supply Chain Dataset CSV file
2. ▶️ Run the notebook/script sequentially
3. 💾 Database file `supply_chain.db` will be created automatically
4. 📈 View generated visualizations for insights
5. 🔍 Query the database for custom analysis

## 🔮 Future Enhancements

- 🤖 Predictive modeling for sales forecasting
- 💵 Customer lifetime value analysis
- 📦 Inventory optimization recommendations
- 📊 Real-time dashboard development
- 🗺️ Advanced geographic mapping with folium/plotly

## 📋 Requirements

```txt
pandas
matplotlib
seaborn
sqlite3
```

## 📄 License

This project is for educational and analytical purposes.

---

**💡 Note**: This analysis provides insights into supply chain operations, helping businesses optimize inventory, improve shipping efficiency, and enhance customer satisfaction.

## 📞 Contact

For questions or collaboration opportunities, feel free to reach out!

---

⭐ **Star this repository if you find it helpful!**
