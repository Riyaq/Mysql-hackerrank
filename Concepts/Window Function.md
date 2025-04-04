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

<br>
Explanation: <br>
<mark>SUM(sale_amount) OVER (ORDER BY sale_date)</mark> is a window function that computes the cumulative sum of sale_amount ordered by sale_date.<br>
The <mark>ORDER BY sale_date</mark> ensures that the rows are ordered by the sale_date before calculating the running total.

-----------------------------------------------------
**2. Rank Sales by Date**
You have a table sales with the following columns:<br>
| sale_date	| sale_amount| 
| ------------- | ------------- |
| 2024-01-01	| 100 |
| 2024-01-02	| 200 |
| 2024-01-03	| 150 |
| 2024-01-04	| 250 |
Solution<br>
```sql
SELECT 
    sale_date,
    sale_amount,
    RANK() OVER (ORDER BY sale_amount DESC) AS sale_rank
FROM 
    sales
ORDER BY 
    sale_date;
```
Output Table - <br>
| sale_date	| sale_amount| 
| ------------- | ------------- |
| 2024-01-01	| 100 | 4 |
| 2024-01-02	| 200 | 2 |
| 2024-01-03	| 150 | 3 |
| 2024-01-04	| 250 | 1 |
<br>
<mark>RANK() OVER (ORDER BY sale_amount DESC)</mark> ranks the rows based on sale_amount, in descending order. <br>
If two rows have the same <mark>sale_amount</mark>, they will receive the same rank, and the next rank will skip accordingly.
