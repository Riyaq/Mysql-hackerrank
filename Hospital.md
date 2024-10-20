***Table — Name — Columns***
Table1 — Patients— patient_id, first_name, last_name, gender, birth_date, city, province_id, allergies, height, weight

Table2 — Admissions — patient_id, admission_date, discharge_date, diagnosis, attending_doctor_id

Table3 — Doctors — doctor_id, first_name, last_name, specialty

Creating table1:
```sql
CREATE TABLE Patients(patient_id int primary key,first_name varchar(20),last_name  varchar(20),gender char,birth_date date,city varchar(20),province_id int,allergies varchar(20),height float,weight float)

```
