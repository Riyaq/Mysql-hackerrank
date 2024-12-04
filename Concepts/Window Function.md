<img width="1178" alt="Screenshot 2024-12-04 at 10 54 04 AM" src="https://github.com/user-attachments/assets/cba45b9c-86c1-4dbd-b581-199d49c5917c">

**Syntax**
```sql
SELECT column_name1, 
 window_function(column_name2)
 OVER([PARTITION BY column_name1] [ORDER BY column_name3]) AS new_column
FROM table_name;
```
**Key Terms**

<img width="1027" alt="Screenshot 2024-12-04 at 10 57 16 AM" src="https://github.com/user-attachments/assets/519e0197-b1ba-4907-a03f-fbe3a8f01a5d">

### 1. Aggregate Window Function -
These functions allow us to perform aggregate operations across a set of rows within the defined window, while still retaining the detail-level data.<br>
This are 5 aggregate function - 
- SUM()<br>
- AVG()
- COUNT()
- MAX()
- MIN()
