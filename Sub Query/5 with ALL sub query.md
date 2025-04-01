### Question
Subquery with ALL Find all employees whose salary is greater than the salary of every employee in the "IT" department. Using the Employees table, write a query to find employees whose salary is greater than the salary of every employee in the "IT" department.


Table -
# Employees Table

| EmployeeID | Name    | Salary  | Department |
|------------|--------|---------|------------|
| 1          | Alice  | 50000   | IT         |
| 2          | Bob    | 60000   | IT         |
| 3          | Charlie| 55000   | HR         |
| 4          | David  | 75000   | Finance    |
| 5          | Emma   | 80000   | Marketing  |
| 6          | Frank  | 62000   | IT         |
| 7          | Grace  | 90000   | Sales      |
| 8          | Hannah | 65000   | Finance    |


## Solution 1
With ALL keyword in a subquery
```sql
SELECT * 
FROM Employees 
WHERE Salary > ALL (
    SELECT Salary 
    FROM Employees 
    WHERE Department = 'IT'
);
```
## Solution 2
 with MAX()
 ```sql
SELECT * 
FROM Employees 
WHERE Salary > (
    SELECT MAX(Salary) 
    FROM Employees 
    WHERE Department = 'IT'
);
```
