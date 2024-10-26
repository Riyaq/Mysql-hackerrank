# Query 1
[584. Find Customer Referee](https://leetcode.com/problems/find-customer-referee/description/?envType=study-plan-v2&envId=top-sql-50) <br>



```SQL
select name
from customer
where referee_id != 2 or referee_id is NULL
```
