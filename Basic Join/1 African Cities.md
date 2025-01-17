Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.<br>
<br>
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.<br>

Link : https://www.hackerrank.com/challenges/african-cities/problem?isFullScreen=true

```sql
SELECT CITY.Name
FROM CITY
JOIN COUNTRY ON CITY.CountryCode = COUNTRY.Code
WHERE COUNTRY.Continent = 'Africa';
```

