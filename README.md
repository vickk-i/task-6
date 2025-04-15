
---

## 📊 Task 6: Sales Trend Analysis Using Aggregations

### 🧩 Objective:
Analyze monthly revenue and order volume using SQL aggregation techniques on the `online_sales` table.

---

### 🗃️ Dataset:
**Table Name:** `online_sales`  
**Columns:**  
- `order_id`  
- `order_date`  
- `product_id`  
- `amount`  
![image](https://github.com/user-attachments/assets/7eae57f4-dd69-4b7c-9bf3-79c7c726f432)

![image](https://github.com/user-attachments/assets/03642dec-8ee7-42dd-9c3a-2348d0bc2e2f)

---

### 🔧 Tools:
- PostgreSQL (pgAdmin 4)

---

### 🧪 SQL Queries and Logic:

#### 1. **Group Orders by Month and Year**
```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS order_year,
    EXTRACT(MONTH FROM order_date) AS order_month
FROM online_sales
GROUP BY 
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date);
```
![image](https://github.com/user-attachments/assets/fd3841d9-d3ce-469f-a6cf-1df1ea939d18)

#### 2. **Extract Only Month from `order_date`**
```sql
SELECT 
    EXTRACT(MONTH FROM order_date) AS order_month
FROM online_sales;
```
![image](https://github.com/user-attachments/assets/5773f963-da2f-4946-94c4-998078964761)

#### 3. **Sort by Year and Month**
```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS order_year,
    EXTRACT(MONTH FROM order_date) AS order_month
FROM online_sales
ORDER BY 
    order_year, 
    order_month;
```
![image](https://github.com/user-attachments/assets/6fe3f6a9-7cd3-46a6-b02c-f7c1b035758e)

#### 4. **Limit Results to Specific Time Range (Feb to Apr 2024)**
```sql
SELECT 
    EXTRACT(YEAR FROM order_date) AS order_year,
    EXTRACT(MONTH FROM order_date) AS order_month
FROM online_sales
WHERE order_date >= '2024-02-01' AND order_date < '2024-05-01'
GROUP BY 
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY 
    order_year, 
    order_month;
```
![image](https://github.com/user-attachments/assets/a55ff8b2-ff7d-446c-a46e-018d4f9c3067)

#### 5. **Count Distinct Orders (Volume)**
```sql
SELECT 
    COUNT(DISTINCT order_id) AS total_orders
FROM online_sales;
```
![image](https://github.com/user-attachments/assets/445c9458-085d-42a3-888f-879e835157d4)

#### 6. **Sum of Revenue**
```sql
SELECT 
    SUM(amount) AS total_revenue
FROM online_sales;
```
![image](https://github.com/user-attachments/assets/ac8e1e9a-06c1-40d2-b0b6-0edc527aa6dd)

---

### 📈 Insights:

- Total number of **distinct orders**: `12`
- Total **revenue** generated: `$2835.00`
- Orders span from **January to June 2024**, and were analyzed month-wise for trends.
- Filters and sorting enabled viewing data across specific months (`Feb-Apr` 2024).

---

### 📎 References:
- SQL Functions: `EXTRACT()`, `COUNT(DISTINCT)`, `SUM()`
- Clauses Used: `GROUP BY`, `ORDER BY`, `WHERE`

---

