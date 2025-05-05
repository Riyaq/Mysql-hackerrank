https://www.hackerrank.com/challenges/contest-leaderboard/problem?isFullScreen=true

### My approach
```sql
SELECT 
    h.hacker_id, 
    h.name, 
    SUM(max_scores.max_score) AS total_score
FROM 
    hackers h
JOIN (
    SELECT 
        hacker_id, 
        challenge_id, 
        MAX(score) AS max_score
    FROM 
        submissions
    GROUP BY 
        hacker_id, 
        challenge_id
) max_scores ON h.hacker_id = max_scores.hacker_id
GROUP BY 
    h.hacker_id, 
    h.name
HAVING 
    SUM(max_scores.max_score) > 0
ORDER BY 
    total_score DESC, 
    h.hacker_id ASC;
```













**Solution 1***
Best appraoch 
```sql
WITH max_scores AS (
    SELECT 
        hacker_id,
        challenge_id,
        MAX(score) AS max_score
    FROM Submissions
    GROUP BY hacker_id, challenge_id
)

SELECT 
    h.hacker_id,
    h.name,
    SUM(ms.max_score) AS total_score
FROM Hackers h
JOIN max_scores ms ON h.hacker_id = ms.hacker_id
GROUP BY h.hacker_id, h.name
HAVING SUM(ms.max_score) > 0
ORDER BY total_score DESC, h.hacker_id ASC;
```

**Solution 2**
Less Optimal
```sql
SELECT h.hacker_id, h.name, SUM(max_score) AS total_score
FROM Hackers h
JOIN (
    SELECT hacker_id, challenge_id, MAX(score) AS max_score
    FROM Submissions
    GROUP BY hacker_id, challenge_id
) ms ON h.hacker_id = ms.hacker_id
GROUP BY h.hacker_id, h.name
HAVING SUM(max_score) > 0
ORDER BY total_score DESC, h.hacker_id ASC;
```
**Solution 3**
```sql
WITH ranked_scores AS (
    SELECT 
        hacker_id,
        challenge_id,
        score,
        RANK() OVER (PARTITION BY hacker_id, challenge_id ORDER BY score DESC) AS rank
    FROM Submissions
)
SELECT 
    h.hacker_id,
    h.name,
    SUM(rs.score) AS total_score
FROM Hackers h
JOIN ranked_scores rs ON h.hacker_id = rs.hacker_id AND rs.rank = 1
GROUP BY h.hacker_id, h.name
HAVING SUM(rs.score) > 0
ORDER BY total_score DESC, h.hacker_id ASC;
```
