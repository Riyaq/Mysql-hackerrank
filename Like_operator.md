1. Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
   
[Link](https://www.hackerrank.com/challenges/weather-observation-station-8/problem?isFullScreen=true)

**Solution**
```sql
Select distinct city from station where city regexp '^[AEIOU].*[aeiou]$';```


2. Query the [list of CITY names](https://www.hackerrank.com/challenges/weather-observation-station-9/problem?isFullScreen=true) from STATION that do not start with vowels. Your result cannot contain duplicates.


**Solution**

```sql
select distinct city from station where city NOT regexp '^[AEIOU]';
