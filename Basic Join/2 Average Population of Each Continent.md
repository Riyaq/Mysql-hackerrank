Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their <br>
respective average city populations (CITY.Population) rounded down to the nearest integer.<br>
<br>
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.<br>
<br>
Link : https://www.hackerrank.com/challenges/average-population-of-each-continent/problem?isFullScreen=true
<br>
```sql
SELECT COUNTRY.Continent, FLOOR(AVG(CITY.Population)) AS AvgCityPopulation
FROM CITY
JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code
GROUP BY COUNTRY.Continent;
```
