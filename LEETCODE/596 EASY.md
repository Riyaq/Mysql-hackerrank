## Classes more than 5 employees 
**Question** <br>
Write a solution to find all the classes that have at least five students.<br>
Input: <br>
Courses table: <br>

| student | class    |
| A       | Math     |
| B       | English  |
| C       | Math     |
| D       | Biology  |
| E       | Math     |
| F       | Computer |
| G       | Math     |
| H       | Math     |
| I       | Math     |

Output: <br>

| class   |

| Math    |

**Answer**
```sql
SELECT class
FROM Courses
GROUP BY class
HAVING count(student)>5 or count(student)=5
```
