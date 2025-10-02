DSA2040A OLAP Assignment

Author: Abdiqalaq Issack - 243

📌 Project Overview

This project demonstrates the design and implementation of a mini OLAP (Online Analytical Processing) system using:
SQLite for relational queries
Pandas for multidimensional analysis
inside a Jupyter Notebook.


The project explores the three main OLAP architectures:

ROLAP (Relational OLAP) – SQL queries on relational tables.

MOLAP (Multidimensional OLAP) – Pivot tables and data cubes for fast slicing/dicing.

HOLAP (Hybrid OLAP) – Combination of ROLAP and MOLAP for scalability and speed.

Key OLAP operations demonstrated:

Slice – Selecting a single dimension or subset of data
Dice – Applying multiple filters across dimensions
Roll-Up – Aggregating data from detailed to higher-level summary
Drill-Down – Breaking aggregated data into more detailed levels

Visualizations are included to show trends and insights clearly.

⚙️ Setup Instructions

Requirements:

Python 3.9+
Jupyter Notebook
Libraries: pandas, numpy, matplotlib, seaborn, sqlite3
Repository structure:

DSA2040A_OLAP_Assignment/
│── olap_assignment.ipynb   # Jupyter Notebook with code + outputs
│── README.md               # Documentation (this file)
│── sales_demo.db           # SQLite database (auto-generated)
│── images/                 # Optional folder for plots/screenshots


🗄️ Data Warehouse Design (Star Schema)

The OLAP system uses a Star Schema:

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


This schema allows analysis across time, products, and categories.

🔍 OLAP Architectures Implemented
1. ROLAP (Relational OLAP)

Implemented using SQL queries on SQLite.

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


3. MOLAP (Multidimensional OLAP)

Uses Pandas pivot tables to create multidimensional cubes.
Example: Revenue by Product Category × Year
pivot = pd.pivot_table(
    sales_df.merge(products_df, on='product_id').merge(dates_df, on='date'),
    values='revenue',
    index='category',
    columns='year',
    aggfunc='sum',
    fill_value=0
)
print(pivot)

Allows fast slicing, dicing, and aggregation.

Heatmaps and other plots provide clear multidimensional insights.

5. HOLAP (Hybrid OLAP)

Combines ROLAP for detailed queries and MOLAP for aggregation.
SQL fetches detailed data
Pandas aggregates and analyzes in-memory
Offers scalability with speed for large datasets


🧩 OLAP Operations Demonstrated

Slice: e.g., sales in Q1 2024
Dice: e.g., Electronics sales in Q1 2024
Roll-Up: Aggregate Product → Category → Year
Drill-Down: Break Year → Quarter → Month

Each operation includes:

Python or SQL code
Table outputs
Visualizations
📊 Visualizations
Bar Chart: Revenue by product category
Heatmap: Revenue cube (Category × Year)
Drill-Down Plot: Revenue trends from Year → Quarter → Month
All done using Matplotlib and Seaborn.


🚀 How to Run

Clone the repository:
git clone https://github.com/yourusername/DSA2040A_OLAP_Assignment.git
Open the notebook:
jupyter notebook olap_assignment.ipynb
Run all cells sequentially.
Optional: Save plots to images/ for GitHub visualization.


🎯 Learning Outcomes
Design a star schema for a data warehouse
Understand ROLAP, MOLAP, HOLAP architectures
Implement OLAP operations practically
Combine SQL + Pandas for hybrid OLAP
Create visualizations to interpret analytical insights
