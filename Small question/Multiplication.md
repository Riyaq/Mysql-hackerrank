# Top Earners
Link : https://www.hackerrank.com/challenges/earnings-of-employees/problem?isFullScreen=true

**Solution**
```sql
SELECT (SALARY*MONTHS) as maxi,count(*) FROM Employee
WHERE SALARY*MONTHS = (SELECT MAX(SALARY* MONTHS)AS maximum FROM Employee)
group by maxi
```
