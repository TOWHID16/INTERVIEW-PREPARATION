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