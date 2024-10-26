# Query 1
[1378. Replace Employee ID With The Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/description/?envType=study-plan-v2&envId=top-sql-50)

```SQL
SELECT unique_id, name FROM Employees
# Unique ID variable doesn't exist will be shown as null, so EmployeeUNI table is put at the  right side of LEFT JOIN function
LEFT JOIN EmployeeUNI using(id);
```
# Query 2
[1068. Product Sales Analysis I](https://leetcode.com/problems/product-sales-analysis-i/description/?envType=study-plan-v2&envId=top-sql-50)

```sql
SELECT p.product_name, s.year, s.price
FROM Sales s 
LEFT JOIN Product p
 ON s.product_id = p.product_id
```
```SQL
SELECT product_name, year, price
FROM Sales
    JOIN Product USING (product_id);
```
