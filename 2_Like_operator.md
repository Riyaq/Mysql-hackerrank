## Leetcode - 3436 Find valid email
Link : https://leetcode.com/problems/find-valid-emails/description/
```sql
SELECT user_id, email
FROM Users
WHERE email REGEXP '^[a-zA-Z0-9_]+@[a-zA-Z]+.com$';
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------

1. [Query the list of CITY names](https://www.hackerrank.com/challenges/weather-observation-station-8/problem?isFullScreen=true) from STATION which have vowels (i.e., a, e, i, o, and u) as **both their first and last characters**. Your result cannot contain duplicates.
   


**Solution 1**
```sql
SELECT CITY FROM STATION
WHERE (CITY like 'A%'or CITY like 'I%' or CITY like 'E%' or CITY like 'O%' or CITY like 'U%') AND 
(CITY like '%a'or CITY like '%e' or CITY like '%i' or CITY like '%o' or CITY like '%u')
```
**Solution 2**
```sql
Select distinct city from station where city regexp '^[AEIOU].*[aeiou]$';
```


--------------------------------------------------------------------------------------------------------------------------------------------------------------
2. [Query the list of CITY names](https://www.hackerrank.com/challenges/weather-observation-station-9/problem?isFullScreen=true) from STATION that **do not start with vowels**. Your result cannot contain duplicates.


**Solution 1**
```sql
SELECT DISTINCT CITY FROM STATION
WHERE NOT (CITY LIKE 'A%' OR CITY LIKE 'E%' OR CITY LIKE 'I%' OR CITY LIKE 'O%' OR CITY LIKE 'U%')
```
**Solution 2**

```sql
select distinct city from station where city NOT regexp '^[AEIOU]';
```

--------------------------------------------------------------------------------------------------------------------------------------------------------------
3.[Query the list of CITY names](https://www.hackerrank.com/challenges/weather-observation-station-10/problem?isFullScreen=true) from STATION that **do not end with vowels**. Your result cannot contain duplicates.

**Solution**
```sql
select distinct city from station where city not regexp '[aeiou]$'
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------
4. [Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels](https://www.hackerrank.com/challenges/weather-observation-station-11/problem?isFullScreen=true). Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT CITY FROM STATION
WHERE CITY NOT REGEXP '^[AEIOU]'
OR CITY NOT REGEXP '[aeiou]$';
```
OR
```sql
SELECT DISTINCT CITY FROM STATION
WHERE NOT (CITY LIKE 'A%' OR CITY LIKE 'E%' OR CITY LIKE 'I%' OR CITY LIKE 'O%' OR CITY LIKE 'U%' )
           OR NOT
            (CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i'  OR CITY LIKE '%o' OR CITY LIKE '%u' );
```

--------------------------------------------------------------------------------------------------------------------------------------------------------------
5. [Query the list of CITY names from STATION that do not start with vowels and do not end with vowels.](https://www.hackerrank.com/challenges/weather-observation-station-12/problem?isFullScreen=true) Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT CITY FROM STATION
WHERE CITY NOT REGEXP '^[AEIOU]'
AND CITY NOT REGEXP '[aeiou]$';
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------
6. [Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345. Round your answer to 4 decimal places.](https://www.hackerrank.com/challenges/weather-observation-station-15/problem?isFullScreen=true)<br>
**Solution**
```sql
SELECT ROUND(LONG_W, 4) FROM STATION
WHERE LAT_N < 137.2345
ORDER BY LAT_N DESC
LIMIT 1;
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------
7. [Query the smallest Northern Latitude (LAT_N) from STATION that is greater than . Round your answer to  decimal places](https://www.hackerrank.com/challenges/weather-observation-station-16/problem?isFullScreen=true)<br>
**Solution**
```sql
SELECT ROUND(LAT_N, 4)
FROM STATION
WHERE LAT_N > 38.7789
ORDER BY LAT_N ASC
LIMIT 1;
```

--------------------------------------------------------------------------------------------------------------------------------------------------------------
8. [Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7780 . Round your answer to 4 decimal places](https://www.hackerrank.com/challenges/weather-observation-station-17/problem?isFullScreen=true)<br>
**Solution**
```sql
SELECT ROUND(LONG_W,4) FROM STATION 
WHERE LAT_N>38.7780 ORDER BY LAT_N ASC
LIMIT 1;
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------
9. [Consider P1(a,b) and P2(c,d) to be two points on a 2D plane](https://www.hackerrank.com/challenges/weather-observation-station-18/problem?isFullScreen=true)<br>

a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).<br>
b happens to equal the minimum value in Western Longitude (LONG_W in STATION).<br>
c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).<br>
d happens to equal the maximum value in Western Longitude (LONG_W in STATION).<br>
Query the Manhattan Distance between points P1 and P2 and round it to a scale of 4 decimal places.<br>
**Solution**
```sql
SELECT ROUND((MAX(LAT_N) - MIN(LAT_N) + MAX(LONG_W) - MIN(LONG_W)), 4) AS D
FROM STATION
```

--------------------------------------------------------------------------------------------------------------------------------------------------------------











--------------------------------------------------------------------------------------------------------------------------------------------------------------
<BR>
<BR>
<img width="700" alt="STATION" src="https://github.com/user-attachments/assets/8ed1e129-1454-456e-8c84-de85f80ea961"><BR>
