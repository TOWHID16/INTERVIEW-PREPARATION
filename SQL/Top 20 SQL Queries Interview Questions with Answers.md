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

### 2. Find Employees With the Same Manager

**Problem:** Write a SQL query to find employees who have the same manager.

**SQL Solution:**
```sql
SELECT e1.employee_id, e1.employee_name, e1.manager_id
FROM employees e1
JOIN employees e2
ON e1.manager_id = e2.manager_id
WHERE e1.employee_id <> e2.employee_id;
