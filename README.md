# SQL-Ecommerce-Analysis

## Objective
The goal of this project is to analyze an e-commerce dataset using SQL to extract meaningful insights about customer behavior, product performance, and sales trends.

---

## Tools & Technologies
- SQL (Oracle SQL)
- Oracle APEX
- Relational Database Concepts

---

## Database Schema
The project is built using a relational database with the following tables:

### Customers
- customer_id (Primary Key)
- name
- city

### Orders
- order_id (Primary Key)
- customer_id (Foreign Key)
- order_date

### Products
- product_id (Primary Key)
- product_name
- category

### Order_Items
- order_id (Foreign Key)
- product_id (Foreign Key)
- quantity
- price

---

## Key SQL Analysis Performed

- Top 3 Products by Revenue   
- City with highest spending
- Repeat Customer Identification 
- Customer Segmentation using CASE statements  
- Monthly Growth Trend

---

## Sample Queries

### 🔹Top 3 Products by Revenue   
```sql
SELECT p.product_name, SUM(oi.quantity * oi.price) AS revenue
FROM products p
JOIN order_items oi ON p.product_id = oi.product_id
GROUP BY p.product_name
ORDER BY revenue DESC
FETCH FIRST 3 ROWS ONLY;
```
### 🔹City with highest spending
```sql
SELECT c.city, SUM(oi.quantity * oi.price) AS total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
JOIN order_items oi ON o.order_id = oi.order_id
GROUP BY c.city
ORDER BY total_spent DESC;
```
### 🔹Repeat Customer Identification 
```sql
SELECT customer_id, COUNT(order_id) AS total_orders
FROM orders
GROUP BY customer_id
HAVING COUNT(order_id) > 1;
```

---

## Project Output
🔹Top 3 Products by Revenue  

<img width="854" height="171" alt="image" src="https://github.com/user-attachments/assets/a0662932-6f00-4bb8-abeb-4239d84e2d1e" />

🔹City with highest spending

<img width="746" height="332" alt="image" src="https://github.com/user-attachments/assets/893458d9-f5d7-4636-8b5a-15f6944bb8e7" />

🔹Repeat Customer Identification 

<img width="772" height="83" alt="image" src="https://github.com/user-attachments/assets/38702a99-7e6a-425b-9600-39878576e5f7" /> 

---

## Key Insights
- A small group of customers contributes a large portion of total revenue
- Electronics category generates the highest revenue
- Repeat customers tend to spend more than one-time buyers
- Sales show an increasing trend over time
- Certain products consistently outperform others

---

## Conclusion
This project demonstrates how SQL can be used to analyze structured data and generate business insights. It highlights the use of joins, aggregations, and conditional logic to solve real-world problems.


