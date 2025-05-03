### CASE and IF ELSE



LINK : https://www.hackerrank.com/challenges/the-report/problem?isFullScreen=true

**Solution**
```sql
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
  IF(Marks >= 70, Name, NULL) ASC,
  IF(Marks < 70, Marks, NULL) ASC;
```
**Solution**
```sql
SELECT 
    CASE 
        WHEN Marks < 70 THEN 'NULL'
        ELSE Name
    END AS Name,
    
    CASE 
        WHEN Marks BETWEEN 90 AND 100 THEN 10
        WHEN Marks BETWEEN 80 AND 89 THEN 9
        WHEN Marks BETWEEN 70 AND 79 THEN 8
        WHEN Marks BETWEEN 60 AND 69 THEN 7
        WHEN Marks BETWEEN 50 AND 59 THEN 6
        WHEN Marks BETWEEN 40 AND 49 THEN 5
        WHEN Marks BETWEEN 30 AND 39 THEN 4
        WHEN Marks BETWEEN 20 AND 29 THEN 3
        WHEN Marks BETWEEN 10 AND 19 THEN 2
        ELSE 1
    END AS Grade,
    
    Marks

FROM Students

ORDER BY 
    Grade DESC,
    CASE 
        WHEN Marks >= 70 THEN Name
        ELSE NULL
    END ASC,
    CASE 
        WHEN Marks < 70 THEN Marks
        ELSE NULL
    END ASC;
```
