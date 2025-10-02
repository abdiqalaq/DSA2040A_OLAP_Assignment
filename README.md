# DSA2040A OLAP Assignment
**Author: Abdiqalaq Issack - 243**

---

## 📌 Project Overview

This project demonstrates the design and implementation of a **mini OLAP (Online Analytical Processing) system**. It explores how OLAP systems can be implemented using relational databases and multidimensional analysis to gain insights from data.

The project focuses on the three main OLAP architectures:

- **ROLAP (Relational OLAP)** – Uses relational databases and SQL-style queries for aggregations.
- **MOLAP (Multidimensional OLAP)** – Uses multidimensional cubes and pivot tables for fast analysis, slicing, and dicing.
- **HOLAP (Hybrid OLAP)** – Combines ROLAP and MOLAP to leverage the strengths of both approaches.

The notebook demonstrates key OLAP operations:

- **Slice** – Selecting a subset of data along a single dimension (e.g., a specific quarter or year).  
- **Dice** – Applying multiple filters across dimensions (e.g., a product category in a specific quarter).  
- **Roll-Up** – Aggregating data from detailed to higher-level summaries (e.g., Product → Category → Year).  
- **Drill-Down** – Breaking aggregated data into more detailed levels (e.g., Year → Quarter → Month).

Visualizations were included to clearly show trends, patterns, and insights.

---

## ⚙️ Setup Instructions

**Requirements:**

- Python 3.9+  
- Jupyter Notebook  
- Libraries: pandas, numpy, matplotlib, seaborn, sqlite3  

**Repository Structure:**


---

## 🗄️ Data Warehouse Design (Star Schema)

The OLAP system uses a **Star Schema** to simplify multidimensional analysis.

### Fact Table: `sales`
- **sale_id:** Primary key, unique identifier for each sale  
- **date:** Foreign key linking to the `dates` dimension  
- **product_id:** Foreign key linking to the `products` dimension  
- **quantity:** Number of units sold  
- **revenue:** Total revenue generated from the sale  

### Dimension Table: `products`
- **product_id:** Primary key, unique product identifier  
- **category:** Product category (e.g., Electronics, Clothing)  
- **name:** Product name  
- **price:** Unit price of the product  

### Dimension Table: `dates`
- **date:** Primary key, sale date  
- **year:** Year of the sale  
- **quarter:** Quarter of the sale  
- **month:** Month of the sale  

This design allows analysis across **time, products, and categories**.

---

## 🔍 OLAP Architectures Implemented

### ROLAP (Relational OLAP)
ROLAP performs aggregations directly on relational tables, simulating traditional database reporting.

### MOLAP (Multidimensional OLAP)
MOLAP uses multidimensional cubes and pivot tables for faster aggregation and analysis. It supports slicing, dicing, and visualization across multiple dimensions.

### HOLAP (Hybrid OLAP)
HOLAP combines the two approaches: it uses relational queries for detailed data and in-memory multidimensional aggregation for summaries. This balances **speed** and **scalability**.

---

## 🧩 OLAP Operations Demonstrated

- **Slice:** Filtering for a specific dimension, e.g., Q1 2024 sales  
- **Dice:** Filtering across multiple dimensions, e.g., Electronics sales in Q1 2024  
- **Roll-Up:** Aggregating from Product → Category → Year  
- **Drill-Down:** Breaking Year → Quarter → Month  

Each operation includes detailed analysis with tables and visualizations in the notebook.

---

## 📊 Visualizations

- **Bar Chart:** Revenue by product category  
- **Heatmap:** Revenue cube (Category × Year)  
- **Drill-Down Plot:** Revenue trends from Year → Quarter → Month  

Visualizations were created using **Matplotlib** and **Seaborn** to enhance insight understanding.

---

## 🚀 How to Run

1. Clone the repository:


2. Open the notebook:


3. Run all cells sequentially. Optional: save plots to `images/` for GitHub visualization.

---

## 🎯 Learning Outcomes

- How to design a **star schema** for a data warehouse  
- Understand **ROLAP, MOLAP, HOLAP architectures**  
- Implement **OLAP operations** practically  
- Combine relational queries with multidimensional analysis (hybrid OLAP)  
- Use visualizations to interpret analytical insights effectively
