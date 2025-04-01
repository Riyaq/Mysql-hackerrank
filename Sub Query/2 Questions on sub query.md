## Single-Row Subquery
***1. Find all employees who earn more than the average salary.***
Given the Employees table with columns employee_id, name, and salary, write a query to select the employees whose salary is higher than the average salary across all employees.

```sql
SELECT name from Employees
where salary > (SELECT avg(salary) from Employees)
```
## Multi-Row Subquery
***2. Find all employees who earn one of the top 3 highest salaries.***
Using the Employees table, find all employees whose salary is within the top 3 highest salaries. Use the IN operator.

```sql
SELECT name, salary
FROM Employees
WHERE salary IN (
    SELECT salary
    FROM Employees
    ORDER BY salary DESC
    LIMIT 3
);
```
If you don't use sub query here  It does not guarantee that you'll get employees who have the top 3 distinct salaries if there are multiple employees with the same salary.<br>
To ensure you're getting the top 3 distinct salaries, use the IN operator with a subquery that returns distinct salaries.
