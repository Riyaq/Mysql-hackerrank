Table code :
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
