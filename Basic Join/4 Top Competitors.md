
## Question


[Click here to get into hacker rank page](https://www.hackerrank.com/challenges/full-score/problem?isFullScreen=true) <br>
Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! <br>
Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. <br>
Order your output in descending order by the total number of challenges in which the hacker earned a full score.<br>
If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.<br>
<br>
<br>

**Observation**
Here is total 4 table and I have to work with all the table at once.<br>
Hence I will use INNER JOIN here to build connection/ JOIN with all four table.<br>

-----------
## Solution 1

```sql
SELECT 
    h.hacker_id,
    h.name 
FROM Submissions s
    INNER JOIN Challenges c on s.challenge_id = c.challenge_id
    INNER JOIN Difficulty d on d.difficulty_level = c.difficulty_level
    INNER JOIN Hackers h on s.hacker_id = h.hacker_id
WHERE d.score = s.score
GROUP BY h.hacker_id,h.name
HAVING COUNT(s.hacker_id) > 1
ORDER BY COUNT(s.challenge_id) desc,s.hacker_id;
```

## Concept
**How to Decide Table Joining Order in SQL**
1. Understand the Business Question First
   For the "top competitors" problem, we need:

* Hackers who achieved perfect scores
* On more than one challenge
* Ordered by challenge count then hacker_id

2. Identify the Central Fact Table
Submissions is your fact table because:
* It contains the actual scores we're evaluating
* All other tables provide context about these submissions
* Most filtering happens based on submission scores
  
3. Follow the Natural Data Relationships
```sql
Submissions → Challenges → Difficulty  (to check perfect scores)
Submissions → Hackers    (to get hacker names)
```
4. Join Strategy Rules
Base Rules:
> 1. Start with the table containing your primary metrics (Submissions in this case)

> 2. Join dimension tables to add context:

- Join Challenges to understand which challenge was submitted

- Join Difficulty to know what a "perfect score" is for that challenge

- Join Hackers to get the names

5. Applied to Our Problem
   ```sql
FROM Submissions s                  -- Central fact table
JOIN Challenges c ON (...)          -- What challenge was this submission for?
JOIN Difficulty d ON (...)          -- What's the perfect score for this challenge?
JOIN Hackers h ON (...)             -- Who made this submission?
```

6. Quick Decision Checklist
1. What's the primary data we're evaluating? → Start with that table

2. What context do we need about each record? → Join those tables next

3. What filtering can we do early? → Apply WHERE clauses after necessary joins

4. What do we need for final output? → Join those tables last

----------------------------------------------



<br>

## Solution 2
```sql
SELECT
S.hacker_id,
name
FROM SUBMISSIONS AS S
    JOIN HACKERS AS H ON S.hacker_id = H.hacker_id
    JOIN Challenges AS C ON S.challenge_id = C.challenge_id
    JOIN Difficulty AS D ON C.difficulty_level = D.difficulty_level

WHERE S.score = D.score
GROUP BY name, S.hacker_id
HAVING count(S.challenge_id) > 1
ORDER BY count(S.challenge_id) DESC, S.hacker_id;
```

