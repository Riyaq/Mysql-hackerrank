1. What is a Common Table Expression (CTE)? How is it different from a subquery?
   
   A CTE is a temporary result set defined using the WITH keyword that can be referenced within a SELECT, INSERT, UPDATE, or DELETE statement.<br>
   * Readability: CTEs make complex queries more readable.

   * Reusability: You can reference a CTE multiple times within the same query (unlike subqueries).

   * Recursion: CTEs support recursive operations, subqueries don’t.

------------------------------------------------------------------------------------
2. Basic Syntax of CTE?
   ```sql
    WITH cte_name AS (
    SELECT column1, column2
    FROM table_name
    WHERE condition
      )
      SELECT * FROM cte_name;
   ```
------------------------------------------------------------------------------------

3. Can you use multiple CTEs in a single query?<br>
Yes. You can define multiple CTEs by separating them with commas.
------------------------------------------------------------------------------------
4. What is a recursive CTE? Give an example.<br>
A recursive CTE is a CTE that refers to itself. It is useful for hierarchical or tree-structured data, like org charts or category trees.
------------------------------------------------------------------------------------
5. When would you use a CTE over a temp table?<br>
  Use a CTE when:

- You need better readability in complex queries.

- You don’t need to persist data across multiple queries.

- You want recursion.

  Use a temp table when:

- You need to reuse intermediate data across multiple queries.

- You need indexes on intermediate results.

- Performance tuning is required for large datasets.



------------------------------------------------------------------------------------
6. Can a CTE be referenced multiple times in a query?<br>
Answer: Yes, that's one of the main advantages of CTEs over subqueries. You can reuse a CTE multiple times, improving readability and performance (in some databases with proper optimization).
------------------------------------------------------------------------------------
7. How do you improve performance using CTE?<br>
Answer:

- By breaking complex queries into readable parts.

- Reducing redundancy by reusing CTEs instead of writing the same subquery multiple times.

- Avoiding unnecessary joins by filtering data early in the CTE.

- Using recursive CTEs to avoid complex loops in procedural logic.





