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
(6,"Ronit","Sen","M","1999-08-20","Kolkata",100,NULL,5.9,90)
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
5. Update the patients table for the allergies column. If the patient’s allergies is null then replace it with ‘NKA’
   ```sql
      Update Patients
     set allergies = "NKA"
     where allergies is null;
   ```
6. Show first name and last name concatenated into one column to show their full name.
   ```sql
      select first_name,last_name,concat(first_name," ",last_name) as full_name
      from patients;
   ```
8. Show how many patients have a birth_date with 1999 as the birth year.
   ```sql
      select count(*) from Patients
      where year(birth_date)=1999;
   ```
9. Show the first_name, last_name, and height of the patient with the greatest height.
    ```sql
       select first_name,last_name, height from patients 
       order by height desc
       LIMIT 1;
    ```
10. Show all columns for patients who have one of the following patient_ids:
1,3,5
   ```sql
      select * from patients
      where patient_id in (1,3,5)
   ```
12. Show all the columns from admissions where the patient was admitted and discharged on the same day.
    ```sql
       select * from Admissions
       where admission_date=discharge_date;
    ```
17. Show unique birth years from patients and order them by ascending.
    ```sql
       select distinct(year(birth_date)) as Year from Patients
       order by Year ASC;
    ```
18. Show unique first names from the patients table which only occurs once in the list.
    ```sql
       SELECT first_name
       FROM patients
       GROUP BY first_name
       HAVING COUNT(first_name) = 1;
    ```
19. Show patient_id and first_name from patients where their first_name start and ends with ‘s’ and is at least 6 characters long.
    ```sql
       SELECT patient_id, first_name
       FROM patients
       where first_name like "S%s" and len(first_name)>=6;
    ```
--------------
### JOINS

20. Show patient_id, first_name, last_name from patients and diagnosis from admissions table. Primary diagnosis is stored in the admissions table.
```sql
   SELECT p.patient_id,p.first_name,p.last_name, a.diagnosis from patients as p
   join admissions as a
   on p.patient_id=a.patient_id;
```
20. Show patient_id, first_name, last_name from patients who’s diagnosis is ‘Fever’. Primary diagnosis is stored in the admissions table.
```sql
   SELECT p.patient_id,p.first_name,p.last_name, a.diagnosis from patients as p
   join admissions as a
   on p.patient_id=a.patient_id
   where diagnosis="Fever";
```
35. Show first_name, last_name, and the total number of admissions attended for each doctor. Every admission has been attended by a doctor.
    ```sql
    SELECT doctors.first_name, doctors.last_name, COUNT(admissions.attending_doctor_id) AS admission_count
    FROM doctors
    JOIN admissions ON doctors.doctor_id = admissions.attending_doctor_id
    GROUP BY doctors.doctor_id, doctors.first_name, doctors.last_name;
    ```
44. Show patient_id, first_name, last_name, and attending doctor’s specialty. Show only the patients who has a diagnosis as ‘Fever’ and the doctor’s first name is ‘Binayak’. Check patients, admissions, and doctors tables for required information.
```sql
   Select patients.patient_id, patients.first_name, patients.last_name, Doctors.specialty
   From patients
   join Admissions
   on patients.patient_id=Admissions.patient_id
   join Doctors
   on Admissions.attending_doctor_id=Doctors.doctor_id

   where diagnosis = "Fever" AND Doctors.first_name="Binayak";
```
45. All patients who have gone through admissions, can see their medical documents on our site. Those patients are given a temporary password after their first admission. Show the patient_id and temp_password. The password must be the following, in order:<br>
 -- patient_id <br>
 -- the numerical length of patient’s last_name <br>
 -- year of patient’s birth_date <br>
```sql
   SELECT p.patient_id, CONCAT(p.patient_id, Length(p.last_name), YEAR(p.birth_date)) AS temp_password
   FROM patients as p
   JOIN admissions as a ON p.patient_id = a.patient_id;
```
------------------------------
22. Show the total amount of male patients and the total amount of female patients in the patients table.
```sql
   select gender, count(*) from patients
   group by gender
```
23. Show the total amount of male patients and the total amount of female patients in the patients table.
    Display the two results in the same row.
```sql
   SELECT COUNT(case when gender="M" then 1 end) as Male,
   COUNT(case when gender="F" then 1 end) as Female
   from patients;
```










