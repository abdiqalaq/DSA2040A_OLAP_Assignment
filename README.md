DSA2040A OLAP Assignment
Author: Abdiqalaq Issack - 243
📌 Project Overview
This project demonstrates the design and implementation of a mini OLAP (Online Analytical Processing) system using SQLite for relational queries and Pandas for multidimensional analysis inside a Jupyter Notebook.
The goal of this project is to provide a hands-on understanding of OLAP systems, exploring the three main architectures:
ROLAP (Relational OLAP) – Relational databases and SQL queries for aggregation and analysis.
MOLAP (Multidimensional OLAP) – Multidimensional cubes and pivot tables for fast analysis and slicing/dicing.
HOLAP (Hybrid OLAP) – Combines ROLAP and MOLAP to leverage the strengths of both approaches.
The notebook demonstrates key OLAP operations:
Slice – Selecting a single dimension or subset of data.
Dice – Applying multiple filters across dimensions.
Roll-Up – Aggregating data from a detailed level to a higher-level summary.
Drill-Down – Breaking aggregated data into more detailed levels.
Visualizations are included to demonstrate trends and insights clearly across dimensions of the data.
⚙️ Setup Instructions
To run this project, you need:
Python 3.9+
Jupyter Notebook
Python libraries: pandas, numpy, matplotlib, seaborn, sqlite3
Repository structure:
DSA2040A_OLAP_Assignment/
│── olap_assignment.ipynb   # Jupyter Notebook with code + outputs
│── README.md               # This file
│── sales_demo.db           # SQLite database (auto-generated)
│── images/                 # Optional folder for plots/screenshots
🗄️ Data Warehouse Design (Star Schema)
The OLAP system is built using a Star Schema for multidimensional analysis.
Fact Table: sales
Column	Description
sale_id	Primary key, unique identifier for each sale
date	Foreign key linking to the dates dimension
product_id	Foreign key linking to the products dimension
quantity	Number of units sold
revenue	Total revenue generated from the sale
Dimension Table: products
Column	Description
product_id	Primary key, unique product identifier
category	Product category (e.g., Electronics, Clothing)
name	Product name
price	Unit price of the product
Dimension Table: dates
Column	Description
date	Primary key, sale date
year	Year of the sale
quarter	Quarter of the sale
month	Month of the sale
This schema enables analyzing revenue and sales across multiple dimensions: time, products, and categories.
🔍 OLAP Architectures Implemented
1. ROLAP (Relational OLAP)
ROLAP is implemented using SQL queries on SQLite tables.
Example Queries:
Average revenue by product category:
SELECT p.category, AVG(s.revenue) AS avg_revenue
FROM sales s
JOIN products p ON s.product_id = p.product_id
GROUP BY p.category;
Total sales by year:
SELECT d.year, SUM(s.revenue) AS total_revenue
FROM sales s
JOIN dates d ON s.date = d.date
GROUP BY d.year;
Best-selling product in each category:
SELECT p.category, p.name, SUM(s.quantity) AS total_sold
FROM sales s
JOIN products p ON s.product_id = p.product_id
GROUP BY p.category, p.name
ORDER BY total_sold DESC;
ROLAP demonstrates how relational databases can efficiently perform aggregation and filtering on large datasets.
2. MOLAP (Multidimensional OLAP)
MOLAP uses Pandas pivot tables to build multidimensional cubes.
Example Cube: Revenue by Product Category × Year
pivot = pd.pivot_table(
    sales_df.merge(products_df, on='product_id').merge(dates_df, on='date'),
    values='revenue',
    index='category',
    columns='year',
    aggfunc='sum',
    fill_value=0
)
print(pivot)
MOLAP allows fast slicing, dicing, and aggregation.
Visualizations like heatmaps provide clear insights across multiple dimensions.
3. HOLAP (Hybrid OLAP)
HOLAP combines ROLAP for detailed data and MOLAP for summary aggregation.
Detailed records are fetched using SQL (ROLAP).
Aggregation and multidimensional analysis are performed in memory using Pandas (MOLAP).
This hybrid approach offers both scalability and speed, especially for large datasets.
🧩 OLAP Operations Demonstrated
Slice – Selecting sales for a specific dimension, e.g., Q1 2024
Dice – Filtering on multiple dimensions, e.g., Electronics in Q1 2024
Roll-Up – Aggregating from Product → Category → Year
Drill-Down – Breaking down from Year → Quarter → Month
Each operation includes:
Python or SQL code
Outputs as tables
Visualizations for clarity
📊 Visualizations
Bar Chart: Revenue by product category
Heatmap: Revenue cube (Category × Year)
Drill-Down Plots: Revenue trends across Year → Quarter → Month
All visualizations are done using Matplotlib and Seaborn.
🚀 How to Run
Clone the repository:
git clone https://github.com/yourusername/DSA2040A_OLAP_Assignment.git
Open the notebook:
jupyter notebook olap_assignment.ipynb
Run all cells sequentially to see outputs and plots.
Optional: Save plots to images/ folder for GitHub visualization.
🎯 Learning Outcomes
By completing this assignment, I learned:
How to design a star schema for a data warehouse
The difference between ROLAP, MOLAP, and HOLAP architectures
How to implement OLAP operations (Slice, Dice, Roll-Up, Drill-Down) practically
How to combine SQL + Pandas to implement a hybrid OLAP system
The importance of visualizations in conveying analytical insights


