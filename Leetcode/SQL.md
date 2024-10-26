# Query 1
[584. Find Customer Referee](https://leetcode.com/problems/find-customer-referee/description/?envType=study-plan-v2&envId=top-sql-50) <br>



```SQL
SELECT name FROM customer
WHERE referee_id != 2 OR referee_id is NULL
```
# Query 2
[1757. Recyclable and Low Fat Products](https://leetcode.com/problems/recyclable-and-low-fat-products/description/?envType=study-plan-v2&envId=top-sql-50)

```sql
SELECT product_id FROM Products
WHERE low_fats="Y" AND recyclable="Y"
ORDER BY product_id;
```
