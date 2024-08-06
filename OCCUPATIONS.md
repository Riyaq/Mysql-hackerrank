1. [Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation.](https://www.hackerrank.com/challenges/occupations/problem?isFullScreen=true)
2.  The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

Note: Print NULL when there are no more names corresponding to an occupation.

**Input Format**
The OCCUPATIONS table is described as follows:<br>
<img width="333" alt="Screenshot 2024-08-06 at 7 40 11 AM" src="https://github.com/user-attachments/assets/09943705-8db7-46fb-be16-3b2d6d12ac98"><br>
Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.

**Sample Input**<br>
<img width="336" alt="Screenshot 2024-08-06 at 7 42 13 AM" src="https://github.com/user-attachments/assets/259d2a6e-6a09-4b53-8537-90519ca92593">
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
