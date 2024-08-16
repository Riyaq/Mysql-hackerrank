1. Find monthly sale and sort it by desc order.
   --
   Input data-<br>
   <img width="165" alt="Screenshot 2024-08-15 at 11 04 32 PM" src="https://github.com/user-attachments/assets/7f0f904d-ec10-474d-904d-ba74d87f9c37">

   **Solution**
   ```sql
    select year(order_date) as year, month(order_date) as month, sum(sales) as total_sale
    from input
    group by year(order_date), month(order_date)
    order by total_sale ASC;
   ```
input_table_query:<br>
create table input(
order_date date,
sales int)

insert into input values(
 "2021-01-01",20 ),
("2021-01-02",32),
("2021-02-08",45),
("2021-02-04",31),
("2021-03-21",33),
("2021-03-06",19),
("2021-04-07",21),
("2021-04-22",10);

   -------------------------------------------------------------------------------------------------
2. Find the candidate best suited for an open data science job. Find candidate who are proficient in SQL Power BI and Python.
   --
   Input data-<br>
   <img width="160" alt="Screenshot 2024-08-15 at 11 15 11 PM" src="https://github.com/user-attachments/assets/3ab1b296-0fd4-4831-9978-b7945bee132d">
   
 **Solution**
```sql
   select candisate_id , count(skills) as skill_count
   from candidate
   where skills in ("Python","SQL","Power BI")
   group by candisate_id
   having skill_count=3;
 ```
   Here IN operator is being used.<br>
Input_query:<br>
create table candidate(
candisate_id int,
skills varchar(20))

insert into candidate values(
101,"Power BI"),
(101,"Python"),
(101,"SQL"),
(102,"Tablue"),
(102,"SQL"),
(108,"SQL"),
(108,"Power BI"),
(108,"Python"),
(104,"Python"),
(104,"Excel");

-------------------------------------------------------------------------------------------------


3. Write a query to swap all 'm' and 'f' values and vice versa in sex column with single update statement and no intermediate temporary table.
   --
 

<img width="201" alt="Screenshot 2024-08-15 at 11 50 57 PM" src="https://github.com/user-attachments/assets/cf94689f-ec1b-4659-a0c9-12a5b7f1520c">

 **Solution**
 ```sql
UPDATE salary
SET
    sex = CASE sex
        WHEN 'm' THEN 'f'
        ELSE 'm'
    END;
```
OR
```sql
update Salary set sex = if(sex='m' , 'f','m');
```
If you get safe update error then run this line :
```sql
SET SQL_SAFE_UPDATES = 0;
```
Here table name is - Salary



-------------------------------------------------------------------------------------------------
4. Write a query to report all the duplicate email. Make sure email feild is not null.
   -
 
<img width="110" alt="Screenshot 2024-08-16 at 10 34 03 AM" src="https://github.com/user-attachments/assets/67d90607-7a47-482e-beae-40859d543dbb">

**Solution**
 ```sql
select email, count(email) from person_data
group by email
having count(email)>1
```

**input_Query**
   create table person_data(
id int,
email varchar(20))

insert into person_data values(
1, "a@b.com"),
(2, "c@b.com"),
(3, "a@b.com");

select * from person_data

-------------------------------------------------------------------------------------------------
5. Write a query to find employees who earn more than their manager.
   --
   
<img width="201" alt="Screenshot 2024-08-16 at 10 43 08 AM" src="https://github.com/user-attachments/assets/2133614a-da8d-4542-abff-7ea064445a0a">

Here I will use SELF JOIN as I have only one table.
**Solution**

Approach I: Using WHERE clause [Accepted]<br>


As this table has the employee's manager information, we probably need to select information from it twice.
```sql
select a.Name as `Employee`
from 
   em1  as `a`,
   em1 as `b`
where
  a.ManagerId = b.Id
  and a.Salary > b.Salary;
```
Approach II: Using JOIN clause [Accepted]<br>


Actually, JOIN is a more common and efficient way to link tables together, and we can use ON to specify some conditions.
```sql
select a.Name as `Employee`
from em1 as a join em1 as b
on a.ManagerId = b.Id
where a.Salary > b.Salary
```

-------------------------------------------------------------------------------------------------
6. Write a solution to report the movies with an odd odd-numbered id and description not as boring.
   -
   <img width="233" alt="Screenshot 2024-08-16 at 11 35 54 AM" src="https://github.com/user-attachments/assets/64e648ff-bf20-451b-ad9b-31966a346232">
**Solution**
```sql
select * from cinema
where
id/2!=0 and description!="Boring"
order by rating desc
```
-------------------------------------------------------------------------------------------------
7. Write a solution to find all the classes that have atleast 5 students.
   -

<img width="116" alt="Screenshot 2024-08-16 at 11 53 47 AM" src="https://github.com/user-attachments/assets/bb545969-6c7f-4ef7-a7b6-7f2894a92130">

**Solution**
```sql
SELECT class
FROM Courses
GROUP BY class
HAVING COUNT(student) >= 5
```







   


