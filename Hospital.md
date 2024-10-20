***Table — Name — Columns*** <br>
[Webpagelink](https://vaibhavkpatel.medium.com/sql-preparation-for-interviews-6b5b6bfec002) <br>
Table1 — Patients— patient_id, first_name, last_name, gender, birth_date, city, province_id, allergies, height, weight

Table2 — Admissions — patient_id, admission_date, discharge_date, diagnosis, attending_doctor_id

Table3 — Doctors — doctor_id, first_name, last_name, specialty

Creating table1:
```sql
CREATE TABLE Patients(patient_id int primary key,first_name varchar(20),last_name  varchar(20),gender char,birth_date date,city varchar(20),province_id int,allergies varchar(20),height float,weight float)
insert into Patients values
(1,"Ronit","Roy","M","1999-03-23","Kolkata",100,NULL,5.5,80),
(2,"Mayank","Sen","M","1995-03-23","Delhi",200,"Yes",5.0,70),
(3,"Shwetha","Ramkrisnppa","F","2000-03-23","Bangalore",30,"Yes",4.8,50),
(4,"Riya","Ghanty","F","1993-03-23","Durgapur",500,NULL,5.1,48),
(5,"Rupa","Sen","F","1990-03-23","Delhi",200,"Yes",5.0,70);
```
Creating table2:
```sql
CREATE TABLE Admissions (patient_id int,admission_date date,discharge_date date, diagnosis varchar(20),attending_doctor_id int);
insert into Admissions values(1,"2024-08-20","2024-08-24","Fever",01),
(2,"2024-08-18","2024-08-25","Dengue",04),
(3,"2024-08-19","2024-08-22","Headache",02),
(4,"2024-08-20","2024-08-23","Fever",01),
(5,"2024-08-13","2024-08-23","Malaria",02),
(6,"2024-08-18","2024-08-23","Blind",03),
(7,"2024-08-16","2024-08-26","Stomach problem",03);
```
Creating table3:
```sql
CREATE TABLE Doctors (doctor_id int,first_name VARCHAR(20),last_name  VARCHAR(20),specialty   VARCHAR(20));

insert into Doctors values
(01,"Binayak","Malakar","General Physician"),
(02,"Souvargya","Ghanashyam","Viarl deseace expert"),
(03,"Anupama","Ghosh Dostidar","Eye specialist"),
(04,"Sri Diganta","Biswar","Viarl deseace expert");
```
-----------------------------------
1. Show first name, last name, and gender of patients whose gender is ‘M’
   ```sql
      SELECT first_name, last_name, gender FROM patients 
      WHERE gender="M";
   ```
2. Show first name and last name of patients who does not have allergies. (null)
   ```sql
      SELECT first_name, last_name FROM patients
      WHERE allergies is NULL;
   ```
3. Show first name of patients that start with the letter ‘R’
   ```sql
      select first_name from Patients
      where first_name like "R%";
   ```
4. Show first name and last name of patients that weight within the range of 40 to 70
   ```sql
      select first_name,last_name, weight
      from patients 
      where weight between 40 and 70;
   ```








   
