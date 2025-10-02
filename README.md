# DSA2040A OLAP Assignment  
**Author: Abdiqalaq Issack - 243**  

---

## 📌 Project Overview

This project demonstrates the design and implementation of a **mini OLAP (Online Analytical Processing) system** using **SQLite** for relational queries and **Pandas** for multidimensional analysis inside a **Jupyter Notebook**.  

The goal of this project is to provide a hands-on understanding of how OLAP systems work and how they can be implemented in practice. It explores the three main OLAP architectures:  

- **ROLAP (Relational OLAP)** – Uses relational databases and SQL queries for aggregation and analysis.  
- **MOLAP (Multidimensional OLAP)** – Uses multidimensional cubes and pivot tables for fast analysis and slicing/dicing of data.  
- **HOLAP (Hybrid OLAP)** – Combines ROLAP and MOLAP to leverage the strengths of both approaches.  

The notebook demonstrates key OLAP operations:  

- **Slice** – Selecting a single dimension or subset of data.  
- **Dice** – Applying multiple filters across dimensions.  
- **Roll-Up** – Aggregating data from a detailed level to a higher-level summary.  
- **Drill-Down** – Breaking aggregated data into more detailed levels.  

Visualizations are included to clearly demonstrate trends and insights across different dimensions of the data.

---

## ⚙️ Setup Instructions

To run this project, you need the following environment:  

- **Python 3.9+**  
- **Jupyter Notebook**  
- Python libraries:  
```bash
pip install pandas numpy matplotlib seaborn sqlite3
### Fact Table: sales
| Column      | Description |
|------------|-------------|
| sale_id    | Primary key, unique identifier for each sale |
| date       | Foreign key linking to the `dates` dimension |
| product_id | Foreign key linking to the `products` dimension |
| quantity   | Number of units sold |
| revenue    | Total revenue generated from the sale |

### Dimension Table: products
| Column      | Description |
|------------|-------------|
| product_id | Primary key, unique product identifier |
| category   | Product category (e.g., Electronics, Clothing) |
| name       | Product name |
| price      | Unit price of the product |

### Dimension Table: dates
| Column  | Description |
|--------|-------------|
| date   | Primary key, sale date |
| year   | Year of the sale |
| quarter| Quarter of the sale |
| month  | Month of the sale |

### ROLAP Example Query
```sql
SELECT p.category, AVG(s.revenue) AS avg_revenue
FROM sales s
JOIN products p ON s.product_id = p.product_id
GROUP BY p.category;


---

### 4️⃣ Keep Lists and Sections
Use `-` or `*` for bullet points:

```markdown
### OLAP Operations Demonstrated
- **Slice** – Selecting sales for a specific dimension, e.g., Q1 2024
- **Dice** – Filtering on multiple dimensions, e.g., Electronics in Q1 2024
- **Roll-Up** – Aggregating from Product → Category → Year
- **Drill-Down** – Breaking down from Year → Quarter → Month


