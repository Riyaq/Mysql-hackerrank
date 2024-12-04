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
# Example on window function with Aggregate 
**1. Running Total** <br>
 Write a query that calculates the running total (cumulative_sum) of the sale_amount for each day, ordered by sale_date.<br>
Table - <br>
| sale_date  | sale_amount |
| ------------- | ------------- |
| 2024-01-01	| 100 |
| 2024-01-02	| 200 |
| 2024-01-03	| 150 |
| 2024-01-04 |250 |
Solution<br>
```sql
SELECT 
    sale_date,
    sale_amount,
    SUM(sale_amount) OVER (ORDER BY sale_date) AS cumulative_sum
FROM 
    sales
ORDER BY 
    sale_date;
```
OutPut Table<br>
| sale_date  | sale_amount |cumulative_sum |
| ------------- | ------------- | ------------ |
| 2024-01-01	| 100 | 100 |
| 2024-01-02	| 200 | 300 |
| 2024-01-03	| 150 | 450|
| 2024-01-04 |250 | 700|
