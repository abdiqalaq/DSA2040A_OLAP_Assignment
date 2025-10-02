# DSA2040A OLAP Assignment  
**Author: Abdiqalaq Issack - 243**  

---

## 📌 Project Overview
This project demonstrates the design and implementation of a **mini OLAP (Online Analytical Processing) system** using **SQLite (for relational queries)** and **Pandas (for multidimensional analysis)** inside a **Jupyter Notebook**.  

The goal is to practically show how the three OLAP architectures (**ROLAP, MOLAP, HOLAP**) work in real life, and to implement the main OLAP operations:  
- **Slice**
- **Dice**
- **Roll-Up**
- **Drill-Down**

Additionally, visualizations are included to help make the data insights more understandable.  

This assignment reflects concepts taught in **DSA2040A** and is implemented in Python for academic and practical learning.

---

## ⚙️ Setup
To get started, you need the following:
- Python 3.9+  
- Jupyter Notebook  
- Libraries:  
  ```bash
  pip install pandas numpy sqlite3 matplotlib seaborn
VS Code or JupyterLab for running the notebook
The repository is structured as follows:
DSA2040A_OLAP_Assignment/
│── olap_assignment.ipynb   # Main Jupyter Notebook with code + outputs
│── README.md               # Documentation (this file)
│── sales_demo.db           # SQLite database (auto-generated)
🗄️ Data Warehouse Design
We use a Star Schema with:
Fact Table: sales
sale_id (Primary Key)
date (FK → dates)
product_id (FK → products)
quantity
revenue
Dimension Table: products
product_id
category
name
price
Dimension Table: dates
date
year
quarter
month
This schema allows us to explore data along multiple dimensions (time, products, categories).
🔍 OLAP Architectures Implemented
1. ROLAP (Relational OLAP)
ROLAP uses SQL queries directly on relational tables to perform aggregations.
Examples implemented:
Average revenue by product category
Total sales by year
Best-selling product in each category
These queries run directly on SQLite, showing how relational databases can support OLAP-style analysis.
2. MOLAP (Multidimensional OLAP)
MOLAP uses data cubes and pivot tables to analyze data in multiple dimensions.
We use Pandas Pivot Tables to create cubes such as:
Revenue by Product Category × Year
Quantity by Product Category × Month
This enables slicing and dicing data very efficiently.
3. HOLAP (Hybrid OLAP)
HOLAP combines both ROLAP and MOLAP.
SQL (ROLAP) is used to fetch detailed data.
Pandas (MOLAP) is used to build summarized pivot tables.
This demonstrates a hybrid approach that balances scalability with multidimensional analysis.
🧩 OLAP Operations Demonstrated
Slice
Select sales for a single year (e.g., 2024 only).
Dice
Filter sales in Q1 2024 for the Electronics category.
Roll-Up
Aggregate from Product → Category → Year.
Drill-Down
Break down from Year → Quarter → Month for deeper insights.
Each operation includes code, output, and explanation in the notebook.
📊 Visualizations
At least two plots are created:
Bar Chart: Revenue by category.
Heatmap: Revenue by Category × Year cube.
Visualizations are done with Matplotlib and Seaborn to clearly represent OLAP results.
📝 Example Queries
SQL (ROLAP) Example
-- Total revenue per category
SELECT p.category, SUM(s.revenue) as total_revenue
FROM sales s
JOIN products p ON s.product_id = p.product_id
GROUP BY p.category;
Pandas Pivot Table (MOLAP) Example
pivot = pd.pivot_table(
    sales_df,
    values='revenue',
    index='category',
    columns='year',
    aggfunc='sum'
)
print(pivot)
🚀 How to Run
Clone the repository:
git clone https://github.com/yourusername/DSA2040A_OLAP_Assignment.git
Open the Jupyter Notebook:
jupyter notebook olap_assignment.ipynb
Run all cells in order.
Check the outputs and plots.
🎯 Learning Outcomes
From this project, I learned:
How to design a star schema for a data warehouse.
The difference between ROLAP, MOLAP, and HOLAP.
How to implement OLAP operations (Slice, Dice, Roll-Up, Drill-Down) in practice.
How to combine SQL + Pandas for hybrid OLAP.
The importance of data visualization in analytical processing.

