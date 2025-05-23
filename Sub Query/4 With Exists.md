### EXISTS Subquery <br>
Find all departments where at least one employee has made a sale.
Using the Employees and Sales tables, find the departments where at least one employee has made a sale. The Sales table has columns sale_id, employee_id, and amount.
<br>
<br>
There are 3 input table<br>
<img width="815" alt="Screenshot 2025-04-01 at 6 43 38 AM" src="https://github.com/user-attachments/assets/a836a55f-5472-4ac6-a018-8e0cf50ed4eb" />
<br>
The desired output table :<br>
<img width="793" alt="Screenshot 2025-04-01 at 6 45 16 AM" src="https://github.com/user-attachments/assets/aa8c394f-58f8-4fff-89d9-8d04696679df" />
<br>
## ANSWER
----------------------
***Solution 1***
Query Using EXISTS
```sql
SELECT DISTINCT D.department_id, D.department_name
FROM Departments D
JOIN Employees E ON D.department_id = E.department_id
WHERE EXISTS (
    SELECT 1 
    FROM Sales S
    WHERE S.employee_id = E.employee_id
);

```
***Solution 2***
Using JOIN Instead of EXISTS
```sql
SELECT D.department_id, D.department_name
FROM Departments D
JOIN Employees E ON D.department_id = E.department_id
JOIN Sales S ON E.employee_id = S.employee_id
GROUP BY D.department_id, D.department_name
HAVING COUNT(S.sale_id) > 0;\
```
***Solution 2***
Using IN sub query
```sql
SELECT department_id, department_name
FROM Departments
WHERE department_id IN (
    SELECT DISTINCT E.department_id
    FROM Employees E
    JOIN Sales S ON E.employee_id = S.employee_id
);
```
