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
# Query
[1581. Customer Who Visited but Did Not Make Any Transactions](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/description/?envType=study-plan-v2&envId=top-sql-50)

```sql
SELECT v.customer_id, COUNT(*) AS count_no_trans
FROM visits v
LEFT JOIN transactions t USING (visit_id)
WHERE t.transaction_id IS NULL
GROUP BY v.customer_id;
```
```SQL
SELECT DISTINCT customer_id,
                count(customer_id) AS count_no_trans
FROM visits v
LEFT JOIN transactions t ON v.visit_id = t.visit_id
WHERE transaction_id IS NULL
GROUP BY customer_id
ORDER BY NULL;
```
```SQL
SELECT customer_id, COUNT(*) as count_no_trans
FROM Visits
WHERE visit_id NOT IN (SELECT DISTINCT visit_id FROM Transactions)
GROUP BY customer_id;
```
