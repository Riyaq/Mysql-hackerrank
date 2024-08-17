1. [Query the Name of any student in STUDENTS who scored higher than Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
Solution](https://www.hackerrank.com/challenges/more-than-75-marks/problem?isFullScreen=true)<br>

**Solution**

```sql
SELECT NAME FROM STUDENTS
WHERE MARKS>75 
ORDER BY RIGHT(NAME, 3), ID;
```
OR
```sql
SELECT NAME FROM STUDENTS
WHERE MARKS>75 
ORDER BY SUBSTRING(NAME, -3), ID;
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------
2. [Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.](https://www.hackerrank.com/challenges/name-of-employees/problem?isFullScreen=true)<br>
**Solution**
```sql
SELECT NAME FROM Employee
ORDER BY NAME ASC;
```

--------------------------------------------------------------------------------------------------------------------------------------------------------------
3. [Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than $2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.](https://www.hackerrank.com/challenges/salary-of-employees/problem?isFullScreen=true)

**Solution**
```sql
SELECT NAME FROM Employee
WHERE SALARY >2000 AND MONTHS<10
ORDER BY employee_id ASC ;
```
