### Medium
**Question** 
Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.

Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.
Link : https://www.hackerrank.com/challenges/harry-potter-and-wands/problem?isFullScreen=false

**Solution 1**
```sql
SELECT W.id, WP.age, W.coins_needed, W.power
FROM Wands W
JOIN Wands_Property WP ON W.code = WP.code



JOIN (
    SELECT WP.age, W.power, MIN(W.coins_needed) AS min_coins
    FROM Wands W
    JOIN Wands_Property WP ON W.code = WP.code
    WHERE WP.is_evil = 0
    GROUP BY WP.age, W.power
) AS MinCost
  ON WP.age = MinCost.age



 AND W.power = MinCost.power
 AND W.coins_needed = MinCost.min_coins
WHERE WP.is_evil = 0
ORDER BY W.power DESC, WP.age DESC;
```

**Solution 2**
```sql
SELECT W.id, WP.age, W.coins_needed, W.power
FROM Wands W
JOIN Wands_Property WP ON W.code = WP.code
WHERE WP.is_evil = 0
AND W.coins_needed = (
    SELECT MIN(W2.coins_needed)
    FROM Wands W2
    JOIN Wands_Property WP2 ON W2.code = WP2.code
    WHERE WP2.is_evil = 0
    AND W2.power = W.power
    AND WP2.age = WP.age
)
ORDER BY W.power DESC, WP.age DESC;
```
