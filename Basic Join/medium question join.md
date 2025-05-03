## Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.
Link : https://www.hackerrank.com/challenges/placements/problem?isFullScreen=true

**Solution**
```sql
SELECT s.name FROM Students s

JOIN Packages sal_s ON s.id = sal_s.id

JOIN Friends f ON s.id = f.id

JOIN Packages sal_bf ON f.friend_id = sal_bf.id

WHERE sal_bf.salary > sal_s.salary
ORDER BY sal_bf.salary;
```

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
