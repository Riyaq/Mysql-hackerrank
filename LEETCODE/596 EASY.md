## Classes more than 5 employees 
**Question** <br>
Write a solution to find all the classes that have at least five students.<br>
LINK : https://leetcode.com/problems/classes-more-than-5-students/ <br>
**Answer**
```sql
SELECT class_name
FROM enrollments
GROUP BY class_name
HAVING count(*)>5 or count(*)=5
```
```sql
SELECT class_name 
FROM enrollments 
WHERE class_name IN (
    SELECT class_name 
    FROM enrollments 
    GROUP BY class_name 
    HAVING COUNT(*) >= 5
);
```
```sql
WITH ClassCounts AS (
    SELECT class_name, COUNT(*) AS student_count
    FROM enrollments
    GROUP BY class_name
)
SELECT class_name FROM ClassCounts WHERE student_count >= 5;
```
