# Query 1
[584. Find Customer Referee](https://leetcode.com/problems/find-customer-referee/description/?envType=study-plan-v2&envId=top-sql-50) <br>


Table: Customer <br>

+-------------+---------+<br>
| Column Name | Type    |<br>
+-------------+---------+<br>
| id          | int     |<br>
| name        | varchar |<br>
| referee_id  | int     |<br>
+-------------+---------+<br>
In SQL, id is the primary key column for this table.<br>
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.<br>
 <br>
<br>
Find the names of the customer that are not referred by the customer with id = 2.<br>
<br>
Return the result table in any order.<br>
<br>
The result format is in the following example.<br>
<br>
 <br>
<br>
Example 1:<br>
<br>
Input: <br>
Customer table:<br>
+----+------+------------+<br>
| id | name | referee_id |<br>
+----+------+------------+<br>
| 1  | Will | null       |<br>
| 2  | Jane | null       |<br>
| 3  | Alex | 2          |<br>
| 4  | Bill | null       |<br>
| 5  | Zack | 1          |<br>
| 6  | Mark | 2          |<br>
+----+------+------------+<br>
Output: <br>
+------+<br>
| name |<br>
+------+<br>
| Will |<br>
| Jane |<br>
| Bill |<br>
| Zack |<br>
+------+<br>









```SQL
select name
from customer
where referee_id != 2 or referee_id is NULL
```
