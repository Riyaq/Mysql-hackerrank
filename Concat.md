1. [Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical](https://www.hackerrank.com/challenges/the-pads/problem?isFullScreen=true)<br>
 (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).<br>

Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format: 
```markup
There are a total of [occupation_count] [occupation]s.
```
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.


**Solution**
```sql
SELECT CONCAT(NAME,"(",SUBSTR(OCCUPATION,1,1),")") 
FROM OCCUPATIONS 
ORDER BY NAME;

SELECT CONCAT("There are a total of ",COUNT(OCCUPATION)," ",LOWER(OCCUPATION),"s.") 
FROM OCCUPATIONS 
GROUP BY OCCUPATION 
ORDER BY COUNT(OCCUPATION), OCCUPATION;
```
