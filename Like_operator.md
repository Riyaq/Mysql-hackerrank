1. [Query the list of CITY names](https://www.hackerrank.com/challenges/weather-observation-station-8/problem?isFullScreen=true) from STATION which have vowels (i.e., a, e, i, o, and u) as **both their first and last characters**. Your result cannot contain duplicates.
   


**Solution**

```sql
Select distinct city from station where city regexp '^[AEIOU].*[aeiou]$';
```





2. [Query the list of CITY names](https://www.hackerrank.com/challenges/weather-observation-station-9/problem?isFullScreen=true) from STATION that **do not start with vowels**. Your result cannot contain duplicates.


**Solution**


```sql
select distinct city from station where city NOT regexp '^[AEIOU]';
```

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
WHERE CITY NOT REGEXP '^[AEIOU].*[aeiou]$';
```
OR
```sql
SELECT DISTINCT CITY FROM STATION
WHERE NOT (CITY LIKE 'A%' OR CITY LIKE 'E%' OR CITY LIKE 'I%' OR CITY LIKE 'O%' OR CITY LIKE 'U%' )
           OR NOT
            (CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i'  OR CITY LIKE '%o' OR CITY LIKE '%u' );
```





