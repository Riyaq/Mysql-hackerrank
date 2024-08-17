Find out the total call duration happened between 2 people
-



<img width="175" alt="Screenshot 2024-08-17 at 1 53 42 AM" src="https://github.com/user-attachments/assets/9d142bd5-a3cc-498e-ae85-f8f1a4f80ce4">



```sql
with cte as(select duration,
LEAST(from_id, to_id) AS person1,
GREATEST(from_id, to_id) AS person2
from calls)

select person1,person2,count(*) as call_count,sum(duration) as total_duration
from cte 
group by person1,person2;
```
