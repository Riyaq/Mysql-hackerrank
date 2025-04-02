Link: https://leetcode.com/problems/customers-who-never-order/description/

**Solution using JOIN**
```sql
SELECT c.name as Customers FROM Customers as c
LEFT JOIN Orders as o
ON c.id=o.customerId
WHERE o.customerId IS NULL
```
**Solution using subquery**
```sql
SELECT c.name as Customers FROM Customers as c
WHERE NOT EXISTS (
    SELECT 1 FROM Orders o
     WHERE o.customerId=c.id
);
```
