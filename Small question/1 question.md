## Find the second highest salary from the Employees table.
<br>
<br>

| id  | name  | salary |
|-----|-------|--------|
| 1   | Alice | 5000   |
| 2   | Bob   | 7000   |
| 3   | Carol | 7000   |
| 4   | Dave  | 6000   |
| 5   | Eve   | 8000   |
<br>
<br>
**Solution** <br>

Using MAX() with Subquery (Universal Approach)

```sql
SELECT MAX(salary) AS second_highest_salary
FROM Employees
WHERE salary < (SELECT MAX(salary) FROM Employees);
```

**Solution** <br>
Using LIMIT with OFFSET

```sql
SELECT DISTINCT salary 
FROM Employees 
ORDER BY salary DESC 
LIMIT 1 OFFSET 1;
```
**Solution** <br>

Using DENSE_RANK() 
```sql
SELECT salary 
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk 
    FROM Employees
) ranked_salaries
WHERE rnk = 2;
```
