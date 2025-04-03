## Classes more than 5 employees 
**Question** <br>
Write a solution to find all the classes that have at least five students.<br>
LINK : https://leetcode.com/problems/classes-more-than-5-students/ <br>
**Answer** <br>
Using Group By / Having <br>
```sql
SELECT class_name
FROM enrollments
GROUP BY class_name
HAVING count(*)>5 or count(*)=5
```
Using Sub query <br>
```sql
SELECT class_name 
FROM (
    SELECT class_name , count(student) as no_of_students
    FROM enrollments 
    GROUP BY class_name 
) sub_table
WHERE no_of_students>=5

);
```
Using CTE <br>
```sql
WITH ClassCounts AS (
    SELECT class_name, COUNT(*) AS student_count
    FROM enrollments
    GROUP BY class_name
)
SELECT class_name FROM ClassCounts WHERE student_count >= 5;
```
Using CTE <br>
```sql
WITH Courses_CTE as (
SELECT class FROM Courses
GROUP BY class
HAVING COUNT(*)>=5
)
SELECT class FROM Courses_CTE
```
