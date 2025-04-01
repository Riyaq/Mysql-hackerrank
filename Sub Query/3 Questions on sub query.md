## Subquery in FROM Clause
Find the department with the highest average salary.
Using a subquery in the FROM clause, find the department with the highest average salary. You have the following tables:

Employees (employee_id, name, salary, department_id)

Departments (department_id, department_name)

**Table : Employees**
|employee_id|name|salary|department_id|
|-----------|----|------|-------------|
|      1     |  Riya  |    20  |     1        |
|      2     |   Priya |   30   |     2        |
|      3     |   Gopa |    40  |       3      |
|      4     | Suvojit |   50   |      1     |
|      5     | Ritwik  |   45   |      2     |

**Table : Departments**
|department_id|department_name|
|-----------|----|
|    1       | IT   |
|    2       |  HR  |
|    3       | Sales |

This question can be done 3 way

***Solution 1***
Using Sub query
```sql
SELECT D.department_id, D.department_name, DeptAvg.max_avg_salary
FROM Departments D
JOIN (
    SELECT department_id, AVG(salary) AS max_avg_salary
    FROM Employees
    GROUP BY department_id
    ORDER BY max_avg_salary DESC
    LIMIT 1
) AS DeptAvg
ON D.department_id = DeptAvg.department_id;
```
***Solution 2***
Window function and CTE
```sql
WITH DeptAvg AS (
    SELECT department_id, AVG(salary) AS avg_salary,
           RANK() OVER (ORDER BY AVG(salary) DESC) AS rnk
    FROM Employees
    GROUP BY department_id
)
SELECT D.department_id, D.department_name, DeptAvg.avg_salary
FROM Departments D
JOIN DeptAvg ON D.department_id = DeptAvg.department_id
WHERE DeptAvg.rnk = 1;

```


***Solution 3***
Using LIMIT with ORDER BY
```sql
SELECT D.department_id, D.department_name, AVG(E.salary) AS avg_salary
FROM Departments D
JOIN Employees E ON D.department_id = E.department_id
GROUP BY D.department_id, D.department_name
ORDER BY avg_salary DESC
LIMIT 1;
```
