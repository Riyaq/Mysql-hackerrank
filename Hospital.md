***Table — Name — Columns***
Table1 — Patients— patient_id, first_name, last_name, gender, birth_date, city, province_id, allergies, height, weight

Table2 — Admissions — patient_id, admission_date, discharge_date, diagnosis, attending_doctor_id

Table3 — Doctors — doctor_id, first_name, last_name, specialty

Creating table1:
```sql
CREATE TABLE Patients(patient_id int primary key,first_name varchar(20),last_name  varchar(20),gender char,birth_date date,city varchar(20),province_id int,allergies varchar(20),height float,weight float)
insert into Patients values
(1,"Ronit","Roy","M","2024-08-20","Kolkata",100,NULL,5.5,80),
(2,"Mayank","Sen","M","2024-08-21","Delhi",200,"Yes",5.0,70),
(3,"Shwetha","Ramkrisnppa","F","2024-08-22","Bangalore",30,"Yes",4.8,50),
(4,"Riya","Ghanty","F","2024-08-21","Durgapur",500,NULL,5.1,48),
(5,"Rupa","Sen","F","2024-08-22","Delhi",200,"Yes",5.0,70);
```
