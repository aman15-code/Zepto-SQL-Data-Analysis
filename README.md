# Zepto E-Commerce Data Analytics Project

## 📌 Project Overview
The goal of this project is to simulate how data analysts in the e-commerce or retail industry work with real-world data using SQL.
This project focuses on building a database, performing exploratory data analysis, cleaning inconsistent data, and extracting business insights.

### Key Objectives
- Set up a **real-world e-commerce inventory database**
- Perform **Exploratory Data Analysis (EDA)** to understand product categories, availability, and pricing patterns
- Implement **data cleaning techniques** to handle null values and inconsistent price formats
- Write **business-driven SQL queries** to derive insights related to pricing, inventory, discounts, and revenue

This project demonstrates practical **data analysis skills used in retail and e-commerce analytics**.

---

# 📁 Dataset Overview
The dataset was sourced from **Kaggle** and originally scraped from **Zepto’s product listings**. It represents a typical e-commerce product catalog dataset.
Each row represents a unique **SKU (Stock Keeping Unit)** for a product.

Duplicate product names may appear because the same product can exist in multiple **package sizes, weights, discounts, or categories**, which is common in real-world retail datasets.

---

# 🧾 Dataset Columns

| Column | Description |
|------|-------------|
| sku_id | Unique identifier for each product entry |
| name | Product name as shown in the app |
| category | Product category such as Fruits, Snacks, Beverages |
| mrp | Maximum Retail Price (converted from paise to ₹) |
| discountPercent | Discount percentage applied |
| discountedSellingPrice | Final selling price after discount |
| availableQuantity | Units available in inventory |
| weightInGms | Product weight in grams |
| outOfStock | Indicates whether the product is out of stock |
| quantity | Number of units per package |

---

# 🔧 Project Workflow

## 1️⃣ Database & Table Creation

```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
```

---

## 2️⃣ Data Import

The dataset was imported using **pgAdmin's CSV import feature**.

Alternatively, the dataset can be loaded using:

```sql
\copy zepto(category,name,mrp,discountPercent,availableQuantity,
discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'data/zepto_v2.csv'
WITH (
FORMAT csv,
HEADER true,
DELIMITER ',',
QUOTE '"',
ENCODING 'UTF8'
);
```

During the import process an **UTF-8 encoding issue** occurred, which was fixed by saving the CSV file in **CSV UTF-8 format**.

---

# 🔍 Data Exploration

The dataset was explored to understand its structure and patterns.

Analysis included:

- Counting the **total number of records**
- Viewing **sample rows** of the dataset
- Checking for **missing or null values**
- Identifying **distinct product categories**
- Comparing **in-stock vs out-of-stock products**
- Detecting **duplicate product names across different SKUs**

---

# 🧹 Data Cleaning

To improve data quality, several cleaning steps were performed:

- Removed rows where **MRP or discounted selling price was zero**
- Converted **MRP and discountedSellingPrice from paise to rupees**
- Ensured **consistent numeric formatting for price columns**

---

# 📊 Business Insights

SQL queries were used to generate business insights such as:

- Top **10 products with the highest discount percentage**
- **High-MRP products** that are currently out of stock
- **Potential revenue estimation** by product category
- Expensive products **(MRP > ₹500) with minimal discount**
- Top **5 categories offering the highest average discounts**
- **Price per gram calculation** to identify value-for-money products
- Grouping products into **Low, Medium, and Bulk weight categories**
- Measuring **total inventory weight by category**

These insights demonstrate how **SQL can support decision-making in retail analytics**.

---
---

⭐ If you found this project useful, feel free to **star the repository**.
