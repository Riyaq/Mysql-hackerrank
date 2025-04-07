Link : https://leetcode.com/problems/employee-bonus/description/ <br>
Code
**Left JOIN**
```sql
SELECT E.name, bonus
FROM Employee AS E
LEFT JOIN Bonus as B
ON E.empId=B.empId
WHERE bonus<1000 OR bonus IS NULL
```
