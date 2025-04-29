## Table code :
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INT,
    salary INT,
    hire_date DATE
);

INSERT INTO employees (employee_id, employee_name, department_id, salary, hire_date) VALUES
(1, 'Alice',   10, 5000, '2020-01-15'),
(2, 'Bob',     10, 7000, '2021-03-22'),
(3, 'Charlie', 10, 7000, '2019-11-05'),
(4, 'David',   20, 6000, '2020-06-17'),
(5, 'Eve',     20, 5500, '2021-07-19'),
(6, 'Frank',   20, 6000, '2021-01-03'),
(7, 'Grace',   30, 8000, '2022-02-25'),
(8, 'Hank',    30, 7500, '2020-04-10'),
(9, 'Ivy',     30, 8000, '2023-05-30');

```
### Question 1
Rank Employees by Salary:
Write a query to assign a rank to each employee based on their salary within their department.
```sql
SELECT
  employee_id,
  department_id,
  salary,
  RANK() OVER (
    PARTITION BY department_id
    ORDER BY salary DESC
  ) AS salary_rank
FROM employees;
```
### Question 2
Get the Highest Salary per Department:
Show all employees, and use a window function to flag those with the highest salary in their department.
```sql
select id, name, department_id, salary,
CASE when 
     salary = max(salary) over(partition by department_id)
     then "Highest"
     else " "
     end as is_highest_salary
from employee
```
### Question 3
Show Previous Salary:
For each employee, show their salary and the previous employee’s salary in the same department ordered by salary.
```sql
SELECT
  id,
  name,
  department_id,
  salary,
  LAG(salary) OVER (
    PARTITION BY department_id
    ORDER BY salary
  ) AS previous_salary
FROM employee;
```
### Question 4
Add Running Total of Salary per Department:
Compute a cumulative salary sum for employees within each department.
```sql
SELECT
  id,
  name,
  department_id,
  salary,
  SUM(salary) OVER (
    PARTITION BY department_id
    ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
  ) AS running_total_salary
FROM employee;
```











