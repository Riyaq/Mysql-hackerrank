1. Rank Employees by Salary within Each Department.
 <br>
   
  | emp_id | emp_name | department | salary |
| ------- | --------- | ---------- | ------ |
| 1       | Alice     | HR         | 60000  |
| 2       | Bob       | HR         | 55000  |
| 3       | Charlie   | HR         | 60000  |
| 4       | David     | IT         | 75000  |
| 5       | Eva       | IT         | 70000  |
| 6       | Frank     | IT         | 70000  |
| 7       | Grace     | Finance    | 80000  |

Code -
```sql
SELECT
  emp_id,
  emp_name,
  department,
  salary,
  RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS salary_rank
FROM
  employees;
```
----------------------------------------------------------------------------
2. Find Top N Salaries per Department
Using the same employees table, find the top 2 highest-paid employees from each department.

**Solution 1**
```sql
WITH ranked_employees AS (
  SELECT emp_id, emp_name, department, salary,
    RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS salary_rank
  FROM employees
)
SELECT emp_id, emp_name, department, salary
FROM ranked_employees
WHERE salary_rank <= 2;
```
**Solution 2**
```sql
SELECT emp_id, emp_name, department, salary
FROM (
  SELECT emp_id, emp_name, department, salary,
    RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS salary_rank
  FROM employees
) AS ranked
WHERE salary_rank <= 2;
```
