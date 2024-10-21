***1. How to Export Table from MySQL  to CSV file.***
-> [Webpage link](https://www.javatpoint.com/mysql-export-table-to-cvs)<br>
   To export the table into a CSV file, we will use the SELECT INTO....OUTFILE statement. This statement is a <br>compliment of the LOAD DATA command, which is used to write data from a table and then export it into a <br>specified file format on the server host. It is to ensure that we have a file privilege to use this syntax.


   ```sql
   SELECT Id, Name, Email, Phone, City FROM employee_detail  
   INTO OUTFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/employee_backup.csv'   
   FIELDS ENCLOSED BY '"'   
   TERMINATED BY ';'   
   ESCAPED BY '"'   
   LINES TERMINATED BY '\r\n';  
```

