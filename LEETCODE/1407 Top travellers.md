Write a solution to report the distance traveled by each user.

Return the result table ordered by travelled_distance in descending order, if two or more users traveled the same distance, order them by their name in ascending order.

Link : https://leetcode.com/problems/top-travellers/description/

```sql
SELECT u.name, COALESCE(sum(r.distance),0) as travelled_distance FROM Users as u
LEFT JOIN Rides as r
ON u.id=r.user_id
group by user_id
order by travelled_distance DESC, name ASC
```
```sql
SELECT u.name, 
       CASE WHEN SUM(r.distance) IS NULL THEN 0 ELSE SUM(r.distance) END AS travelled_distance
FROM Users AS u
LEFT JOIN Rides AS r
ON u.id = r.user_id
GROUP BY u.id, u.name
ORDER BY travelled_distance DESC, name ASC;
```
