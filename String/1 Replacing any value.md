Q. Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

[Link of Hacker rank](https://www.hackerrank.com/challenges/the-blunder/problem?isFullScreen=true)

```SQL
SELECT CEIL(AVG(SALARY) - AVG(CAST(REPLACE(SALARY, '0', '') AS UNSIGNED))) AS Error
FROM EMPLOYEES;
```

**Cast** : This converts the modified salary (after removing 0 s) back to a number/Integer.
