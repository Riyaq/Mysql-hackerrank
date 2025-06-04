# You have given two table lets play with this -

**Students**

| Id  | Name |Marks |
| ------------- | ------------- |------------- |
| 1  | Riya  | 90 |
|  2 | Suvo  | 89 |

**Grades**
| Grade  | Min_Mark |Max_Mark |
| ------------- | ------------- |------------- |
| 1  | 0  | 9 |
|  2 | 10  | 19 |

**Question :**
generate a report containing three columns: Name, Grade and Mark. <br>
1. Doesn't want the NAMES of those students who received a grade lower than 8. <br>
2. The report must be in descending order by grade -- i.e. higher grades are entered first. <br>
3. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. <br>
4. If the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order.<br>
5. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.<br>
<br>
<br>
Link : https://www.hackerrank.com/challenges/the-report/problem?isFullScreen=true

```SQL
SELECT 
  IF(Marks >= 70, Name, 'NULL') AS Name,
  CASE 
    WHEN Marks >= 90 THEN 10
    WHEN Marks >= 80 THEN 9
    WHEN Marks >= 70 THEN 8
    WHEN Marks >= 60 THEN 7
    WHEN Marks >= 50 THEN 6
    WHEN Marks >= 40 THEN 5
    WHEN Marks >= 30 THEN 4
    WHEN Marks >= 20 THEN 3
    WHEN Marks >= 10 THEN 2
    ELSE 1
  END AS Grade,
  Marks
FROM Students
ORDER BY 
  Grade DESC,
  IF(Marks >= 70, Name, NULL) ASC;
```
------------------------------------
### Solution 2
```sql
SELECT 
    CASE 
        WHEN Grades.Grade < 8 THEN NULL 
        ELSE Students.Name 
    END AS Name,
    Grades.Grade,
    Students.Marks
FROM 
    Students
JOIN 
    Grades ON Students.Marks BETWEEN Grades.Min_Mark AND Grades.Max_Mark
ORDER BY 
    Grades.Grade DESC,
    CASE 
        WHEN Grades.Grade >= 8 THEN Students.Name 
        ELSE NULL 
    END ASC,
    CASE 
        WHEN Grades.Grade < 8 THEN Students.Marks 
        ELSE NULL 
    END ASC;
```
----------------------
### Solution 3
```sql
SELECT 
    IF(Grades.Grade < 8, NULL, Students.Name) AS Name,
    Grades.Grade,
    Students.Marks
FROM 
    Students
JOIN 
    Grades ON Students.Marks BETWEEN Grades.Min_Mark AND Grades.Max_Mark
ORDER BY 
    Grades.Grade DESC,
    IF(Grades.Grade >= 8, Students.Name, NULL) ASC,
    IF(Grades.Grade < 8, Students.Marks, NULL) ASC;
```
