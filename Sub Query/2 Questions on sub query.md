## Single-Row Subquery
***Find all employees who earn more than the average salary.*** <br>
Given the Employees table with columns employee_id, name, and salary, write a query to select the employees whose salary is higher than the average salary across all employees.

```sql
SELECT name from Employees
where salary > (SELECT avg(salary) from Employees)
```
## Multi-Row Subquery
***Find all employees who earn one of the top 3 highest salaries.*** <br>
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

## Correlated Subquery
***Find employees who earn more than the average salary in their department.*** <br>
Given the Employees table, find employees who earn more than the average salary in their respective department. The table has the columns employee_id, name, salary, and department_id.

```sql
SELECT name, salary, department_id
FROM Employees E1
WHERE salary > (
    SELECT AVG(salary)
    FROM Employees E2
    WHERE E1.department_id = E2.department_id
);
```
