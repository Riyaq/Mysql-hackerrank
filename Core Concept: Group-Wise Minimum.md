We need to find, for each unique combination of (age, power), the wand with the lowest coins_needed. This is a classic **"group-wise minimum"** problem in SQL.<br>

### QUESTION 
/*
determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.
*/




[Link](https://www.hackerrank.com/challenges/harry-potter-and-wands/problem?isFullScreen=false) <br>
**Solution**

Path - Basic Join/medium question join/Ollivander's Inventory.md <br>
[Link](https://github.com/Riyaq/Mysql-hackerrank/blob/main/Basic%20Join/medium%20question%20join/Ollivander's%20Inventory.md)
____________________________________________________________
<img width="646" alt="Screenshot 2025-05-04 at 8 33 00 AM" src="https://github.com/user-attachments/assets/6bf7ea24-0358-4b56-8b49-1623562c9fa4" />
<img width="849" alt="Screenshot 2025-05-04 at 8 38 03 AM" src="https://github.com/user-attachments/assets/31ab1b40-24e7-4a4c-a0f9-6831c9490347" />
<img width="777" alt="Screenshot 2025-05-04 at 8 38 22 AM" src="https://github.com/user-attachments/assets/7f5f5e94-f0c1-4ecf-96af-9af73baf6125" />
<img width="830" alt="Screenshot 2025-05-04 at 8 39 11 AM" src="https://github.com/user-attachments/assets/69f14bea-5a8c-4006-bc73-06a838b89f13" />
<img width="915" alt="Screenshot 2025-05-04 at 8 39 50 AM" src="https://github.com/user-attachments/assets/6c993c46-d96a-450e-94b0-41ca66d07b75" />

**Why This Works**
The key is the correlated subquery - it re-calculates for each row:

1.Takes the current row's age and power

2.Finds all wands with that same age and power

3.Returns the minimum coins_needed from that group

4.Only keeps rows where the current wand's coins_needed matches that minimum

5.This ensures we get exactly one wand (the cheapest) for each (age, power) combination.

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
### Solution 2: For MySQL 8.0+ (With CTEs)
If you can upgrade, this is cleaner:
```sql
WITH ranked_wands AS (
    SELECT 
        W.id, 
        WP.age, 
        W.coins_needed, 
        W.power,
        ROW_NUMBER() OVER (
            PARTITION BY WP.age, W.power 
            ORDER BY W.coins_needed
        ) AS rn
    FROM Wands W
    JOIN Wands_Property WP ON W.code = WP.code
    WHERE WP.is_evil = 0
)
SELECT id, age, coins_needed, power
FROM ranked_wands
WHERE rn = 1
ORDER BY power DESC, age DESC;
```
