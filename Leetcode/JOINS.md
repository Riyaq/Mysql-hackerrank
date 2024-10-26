# Query 1
[1378. Replace Employee ID With The Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/description/?envType=study-plan-v2&envId=top-sql-50)

```SQL
SELECT unique_id, name FROM Employees
    # Unique ID variable doesn't exist will be shown as null, so EmployeeUNI table is put at the  right side of LEFT JOIN function
    LEFT JOIN EmployeeUNI using(id);
```
