Link : https://leetcode.com/problems/department-highest-salary/submissions/1594770801/

```sql
select d.Name as Department, e.Name as Employee, Salary from Department d 
join Employee e
on e.DepartmentId = d.Id
where (e.Salary, e.DepartmentId) in (
          select max(e.Salary), e.DepartmentId 
          from Employee e 
          group by e.DepartmentId)
```
