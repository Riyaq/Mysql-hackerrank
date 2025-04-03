## Classes more than 5 employees 
**Question** <br>
Write a solution to find all the classes that have at least five students.<br>
LINK : https://leetcode.com/problems/classes-more-than-5-students/
**Answer**
```sql
SELECT class
FROM Courses
GROUP BY class
HAVING count(student)>5 or count(student)=5
```
