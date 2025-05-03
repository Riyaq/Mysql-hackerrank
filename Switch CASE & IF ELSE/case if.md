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
