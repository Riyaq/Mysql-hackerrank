**Type of Triangle**
---------------------
[Write a query identifying the type of each record in the TRIANGLES table using its three side lengths.](https://www.hackerrank.com/challenges/what-type-of-triangle/problem?isFullScreen=true)

**Solution**
```sql
SELECT CASE
      WHEN (A+B<=C) OR (A+C<=B) OR (C+B<=A) THEN 'Not A Triangle'
      WHEN (A=B) AND (B=C) AND (C=A) THEN 'Equilateral'
      WHEN (A=B) OR (B=C) OR (A=C) THEN 'Isosceles'
      ELSE 'Scalene'
  END
FROM TRIANGLES;
```

--------------------------------------------------------------------------------------------------------------------------------------------------------------
**The PADS**
--------------


[Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical](https://www.hackerrank.com/challenges/the-pads/problem?isFullScreen=true)<br>
 (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).<br>

Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format: 
```markup
There are a total of [occupation_count] [occupation]s.
```
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

Given a table OCCUPATIONS that holds data for three fields namely Column, Type.<br>
<img width="219" alt="Screenshot 2024-08-06 at 7 14 21 AM" src="https://github.com/user-attachments/assets/bf33912d-a932-46f1-8e98-a2b4a21d7fb9">

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

















--------------------------------------------------------------------------------------------------------------------------------------------------------------
**Occupations**
-----------------
[Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation.](https://www.hackerrank.com/challenges/occupations/problem?isFullScreen=true)<br>
   The output column headers should be Doctor, Professor, Singer, and Actor, respectively.<br>
Note: Print NULL when there are no more names corresponding to an occupation


**Input Format**
The OCCUPATIONS table is described as follows:<br>
<img width="333" alt="Screenshot 2024-08-06 at 7 40 11 AM" src="https://github.com/user-attachments/assets/09943705-8db7-46fb-be16-3b2d6d12ac98"><br>
Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.

**Sample Input**<br>
<img width="336" alt="Screenshot 2024-08-06 at 7 42 13 AM" src="https://github.com/user-attachments/assets/259d2a6e-6a09-4b53-8537-90519ca92593"><br>
**Sample Output**
```markup
Jenny    Ashley     Meera  Jane
Samantha Christeen  Priya  Julia
NULL     Ketty      NULL   Maria
```
**Explanation**

The first column is an alphabetically ordered list of Doctor names.
The second column is an alphabetically ordered list of Professor names.
The third column is an alphabetically ordered list of Singer names.
The fourth column is an alphabetically ordered list of Actor names.
The empty cell data for columns with less than the maximum number of names per occupation (in this case, the Professor and Actor columns) are filled with NULL values.

```sql
SELECT
  MAX(CASE WHEN Occupation = 'Doctor' THEN Name END) AS Doctor,
  MAX(CASE WHEN Occupation = 'Professor' THEN Name END) AS Professor,
  MAX(CASE WHEN Occupation = 'Singer' THEN Name END) AS Singer,
  MAX(CASE WHEN Occupation = 'Actor' THEN Name END) AS Actor
FROM (
  SELECT
    ROW_NUMBER() OVER (PARTITION BY Occupation ORDER BY Name) AS rn,
    Name,
    Occupation
  FROM OCCUPATIONS
) AS sub
GROUP BY rn
ORDER BY rn;
```


--------------------------------------------------------------------------------------------------------------------------------------------------------------
**Binary tree nodes**
-----------------
[You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.](https://www.hackerrank.com/challenges/binary-search-tree-1/problem?isFullScreen=true)<br>

<img width="603" alt="Screenshot 2024-08-06 at 8 07 33 AM" src="https://github.com/user-attachments/assets/8a548a35-c647-43fc-9c40-fe546604d041"><br>
**Solution**
```sql
select N,
       if(P is null, 'Root', if((select count(*) from BST where P = B.N)> 0, 'Inner', 'Leaf')) 
from BST as B 
order by N;
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------
New Companies
--------------
[Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy](https://www.hackerrank.com/challenges/the-company/problem?isFullScreen=true)
<br>

**Note:**

The tables may contain duplicate records.
The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.





```sql
SELECT
    c.company_code,
    c.founder,
    COUNT(DISTINCT lm.lead_manager_code) AS total_lead_managers,
    COUNT(DISTINCT sm.senior_manager_code) AS total_senior_managers,
    COUNT(DISTINCT m.manager_code) AS total_managers,
    COUNT(DISTINCT e.employee_code) AS total_employees
FROM
    Company c
    LEFT JOIN Lead_Manager lm ON c.company_code = lm.company_code
    LEFT JOIN Senior_Manager sm ON lm.lead_manager_code = sm.lead_manager_code AND lm.company_code = sm.company_code
    LEFT JOIN Manager m ON sm.senior_manager_code = m.senior_manager_code AND sm.lead_manager_code = m.lead_manager_code AND sm.company_code = m.company_code
    LEFT JOIN Employee e ON m.manager_code = e.manager_code AND m.senior_manager_code = e.senior_manager_code AND m.lead_manager_code = e.lead_manager_code AND m.company_code = e.company_code
GROUP BY
    c.company_code,
    c.founder
ORDER BY
    c.company_code;
```


