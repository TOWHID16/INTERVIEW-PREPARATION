# Top 20 SQL Queries Interview Questions with Answers

[top 20 Questions](https://skphd.medium.com/top-20-sql-queries-interview-questions-with-answers-56e70e4878d2)

---

### 1. Find the 2nd Highest Salary

**Problem:** Write a query to find the 2nd highest salary from an employee table.

**SQL Solution:**
```sql
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

### 2. Find Employees With the Same Manager

**Problem:** Write a SQL query to find employees who have the same manager.

**SQL Solution:**
```sql
SELECT e1.employee_id, e1.employee_name, e1.manager_id
FROM employees e1
JOIN employees e2
ON e1.manager_id = e2.manager_id
WHERE e1.employee_id <> e2.employee_id;
```

### 3. Find the Most Recent Transaction for Each Customer.

**Problem:** Write a query to find the most recent transaction for each customer.

**SQL Solution:**
```sql
SELECT *
FROM transactions t1
WHERE transaction_date = (
    SELECT MAX(transaction_date)
    FROM transactions t2
    WHERE t1.customer_id = t2.customer_id
);
```


### 4. Find Department Total Salary Above a Certain Value

**Problem:** Write a query to find the total salary of each department and display departments with a total salary greater than a specified value (e.g., 50,000).

**SQL Solution:**
```sql
SELECT department_id, SUM(salary) AS total_salary
FROM employees
GROUP BY department_id
HAVING total_salary > 50000;
```

### 5. Count Employees Hired Per Month and Year

**Problem:** Write a query to get the total number of employees hired per month and year.

**SQL Solution:**
```sql
SELECT YEAR(hire_date) AS year, MONTH(hire_date) AS month, COUNT(*) AS total_hires
FROM employees
GROUP BY year, month;
```

### 6. Find Employees Earning More Than Their Department's Average Salary.

**Problem:** Write a query to display all employees who earn more than the average salary for their department.

**SQL Solution:**
```sql
SELECT *
FROM employees e
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
    WHERE department_id = e.department_id
);
```

### 7. Find the Second-Lowest Salary Without LIMIT or OFFSET.

**Problem:** Write a query to get the second-lowest salary from the employee table without using LIMIT or OFFSET.

**SQL Solution:**
```sql
SELECT MIN(salary)
FROM employees
WHERE salary >
(SELECT MIN(salary)
FROM employees);
```

### 8. List Products That Have Never Been Ordered.

**Problem:** Write a query to list all products that have never been ordered (assuming an ‘orders’ table and a ‘products’ table).

**SQL Solution:**
```sql
SELECT p.product_id, p.product_name
FROM products p
LEFT JOIN orders o
ON p.product_id = o.product_id
WHERE o.product_id IS NULL;
```

### 9. List All Employees Who Are Also Managers.

**Problem:** Write a query to list all the employees who are also managers.

**SQL Solution:**
```sql
SELECT DISTINCT e.*
FROM employees e
JOIN employees m
ON e.employee_id = m.manager_id;
```

### 10. Find Employees Who Joined in the Same Month and Year.

**Problem:** Write a query to find employees who have joined in the same month and year.

**SQL Solution:**
```sql
SELECT e1.employee_id, e1.employee_name, e1.hire_date
FROM employees e1
JOIN employees e2
ON YEAR(e1.hire_date) = YEAR(e2.hire_date)
AND MONTH(e1.hire_date) = MONTH(e2.hire_date)
AND e1.employee_id <> e2.employee_id;
```

### 11. Find Employees Older Than Their Department's Average Age.

**Problem:** Write a SQL query to get a list of employees who are older than the average age of employees in their department.

**SQL Solution:**
```sql
SELECT *
FROM employees e
WHERE age > (
    SELECT AVG(age)
    FROM employees
    WHERE department_id = e.department_id
);
```

### 12. Find the Employee with the Longest Tenure.

**Problem:** Write a query to display the employee(s) with the longest tenure at the company.

**SQL Solution:**
```sql
SELECT *
FROM employees
ORDER BY hire_date ASC
LIMIT 1;
```

### 13. Delete Records Where a Column Value is NULL.

**Problem:** Write a query to delete all records from a table where the column value is NULL.

**SQL Solution:**
```sql
DELETE FROM table_name
WHERE column_name IS NULL;
```

### 14. Find Pairs of Products Ordered Together.

**Problem:** Write a query to find all pairs of products that were ordered together at least once.

**SQL Solution:**
```sql
SELECT o1.product_id AS product1, o2.product_id AS product2, COUNT(*) AS frequency
FROM orders o1
JOIN orders o2
ON o1.order_id = o2.order_id
AND o1.product_id < o2.product_id
GROUP BY product1, product2
HAVING COUNT(*) > 0;
```

### 15. Find Average Order Value by Customer Per Month.

**Problem:** Write a query to find the average order value by customer for each month.

**SQL Solution:**
```sql
SELECT customer_id, YEAR(order_date) AS year, MONTH(order_date) AS month,
AVG(order_amount) AS avg_order_value
FROM orders
GROUP BY customer_id, year, month;
```

### 16. Find Customers Who Purchased Every Month for the Past Year.

**Problem:** Write a query to identify customers who made a purchase every month for the past year.

**SQL Solution:**
```sql
SELECT customer_id
FROM orders
WHERE order_date >= DATE_SUB(CURDATE(), INTERVAL 1 YEAR)
GROUP BY customer_id
HAVING COUNT(DISTINCT MONTH(order_date)) = 12;
```

### 17. Find Total Revenue by Region Per Quarter.

**Problem:** Write a query to find the total revenue for each region in a given quarter.

**SQL Solution:**
```sql
SELECT region, QUARTER(order_date) AS quarter, SUM(order_amount) AS total_revenue
FROM orders
GROUP BY region, quarter;
```

### 18. Find the First Purchase Date of Each Customer.

**Problem:** Write a query to find the first purchase date of each customer.

**SQL Solution:**
```sql
SELECT customer_id, MIN(order_date) AS first_purchase_date
FROM orders
GROUP BY customer_id;
```

### 19. Find the Nth Highest Salary.

**Problem:** Write a query to find the ‘Nth’ highest salary from the employee table (e.g., 5th highest salary).

**SQL Solution:**
```sql
-- Replace N with the desired rank, e.g., 4 for the 5th highest salary (since OFFSET is 0-indexed).
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET (N-1);
```

