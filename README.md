# 📊 Superstore SQL Analytics Project

Welcome to the **Superstore SQL Analytics Project**!  
This project uses SQL to analyze a retail dataset and uncover meaningful insights for business decision-making. It includes sales trends, customer behavior, discount effectiveness, and geographic performance analysis.

---

## 🧾 Project Overview

This SQL project is based on the **Superstore Sales Dataset**, a popular retail dataset used for business intelligence case studies. Using MySQL, we clean the data, load it into a structured table, and run insightful queries that mimic real-world business reporting.

---

## 🧰 Tools & Technologies

- **Database**: MySQL 8.x  
- **Query Language**: SQL  
- **Environment**: MySQL Workbench / XAMPP / CLI  
- **Data Source**: [Kaggle - Superstore Sales Dataset](https://www.kaggle.com/datasets/annavnash/superstore-sales)

---

## 🏗️ Project Setup Instructions

### 1. Create Database & Select
```sql
CREATE DATABASE SUPERSTORE;
USE SUPERSTORE;
2. Enable CSV Import
SET GLOBAL local_infile = 1;
SHOW VARIABLES LIKE 'secure_file_priv';
3. Create Table s1

CREATE TABLE s1 (
    Row_ID INT,
    Order_ID VARCHAR(20),
    Order_Date DATE,
    Order_Month TINYINT,
    Order_Month_Name VARCHAR(15),
    Order_Year SMALLINT,
    Ship_Date DATE,
    Ship_Month TINYINT,
    Ship_Month_Name VARCHAR(15),
    Ship_Year SMALLINT,
    Ship_Mode VARCHAR(50),
    Customer_ID VARCHAR(20),
    Customer_Name VARCHAR(100),
    Segment VARCHAR(50),
    Country VARCHAR(50),
    City VARCHAR(50),
    State VARCHAR(50),
    Postal_Code VARCHAR(10),
    Region VARCHAR(50),
    Product_ID VARCHAR(20),
    Category VARCHAR(50),
    Sub_Category VARCHAR(50),
    Product_Name VARCHAR(200),
    Sales DECIMAL(10,2),
    Quantity INT,
    Discount DECIMAL(4,2),
    Profit DECIMAL(10,2)
);
4. Load the Dataset
LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/superstore.csv'
INTO TABLE s1
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 LINES;
📊 Key Analysis Queries
🗓️ Time-Based Analysis
Total Sales and Profit by Year & Month

Sales by Weekday

🛍️ Product & Category Performance
Top 10 Products by Sales

Sub-Category Sales Ranking

High Sales, Low Profit Products

📦 Shipping Insights
Average Order-to-Ship Days

Ship Mode Utilization

🌍 Geographic Trends
Regional Sales & Profit

States & Cities with Negative Profits

👥 Customer Behavior
Top Customers by Profit

Segment-Wise Profitability

💸 Discount & Profitability
Profit vs Discount Trends

Optimal Discount Levels

Discount Ranges Causing Losses

🧠 Sample Queries
-- Total Sales and Profit by Year
SELECT Order_Year, SUM(Sales) AS TOTAL_SALES, SUM(Profit) AS TOTAL_PROFIT
FROM s1
GROUP BY Order_Year
ORDER BY Order_Year;

-- Top 10 Products by Sales
SELECT Product_Name, SUM(Sales) AS Top_10_Product
FROM s1
GROUP BY Product_Name
ORDER BY Top_10_Product DESC
LIMIT 10;

-- Cities with Negative Profit
SELECT City, Profit FROM s1 WHERE Profit < 0 ORDER BY Profit ASC;
🏆 Outcomes & Insights
✅ Identified best-selling products and high-profit segments
✅ Measured shipping efficiency and regional performance
✅ Explored discount thresholds that lead to profit or loss
✅ Provided strong foundations for building a Sales KPI Dashboard

📌 Notes
You must disable safe updates temporarily to update the Weekday column:

SET SQL_SAFE_UPDATES = 0;
UPDATE s1 SET Weekday = DAYNAME(Order_Date);
SET SQL_SAFE_UPDATES = 1;
📬 Contact
Gulshan Kumar
📧 gulshankumar02985@gmail.com
🔗 https://www.linkedin.com/in/gulshankumar01/
🐙 https://github.com/GULSHANKUMAR6079

🪪 License
This project is licensed under the MIT License.

📢 Contribute
Pull requests are welcome! Feel free to fork this repo, explore deeper queries, and submit improvements
