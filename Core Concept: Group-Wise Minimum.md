We need to find, for each unique combination of (age, power), the wand with the lowest coins_needed. This is a classic "group-wise minimum" problem in SQL.<br>
[Link](https://www.hackerrank.com/challenges/harry-potter-and-wands/problem?isFullScreen=false) <br>
**Solution**
Path - Basic Join/medium question join/Ollivander's Inventory.md
[Link](https://github.com/Riyaq/Mysql-hackerrank/blob/main/Basic%20Join/medium%20question%20join/Ollivander's%20Inventory.md)
____________________________________________________________
<img width="646" alt="Screenshot 2025-05-04 at 8 33 00 AM" src="https://github.com/user-attachments/assets/6bf7ea24-0358-4b56-8b49-1623562c9fa4" />
<img width="849" alt="Screenshot 2025-05-04 at 8 38 03 AM" src="https://github.com/user-attachments/assets/31ab1b40-24e7-4a4c-a0f9-6831c9490347" />
<img width="777" alt="Screenshot 2025-05-04 at 8 38 22 AM" src="https://github.com/user-attachments/assets/7f5f5e94-f0c1-4ecf-96af-9af73baf6125" />
<img width="830" alt="Screenshot 2025-05-04 at 8 39 11 AM" src="https://github.com/user-attachments/assets/69f14bea-5a8c-4006-bc73-06a838b89f13" />
<img width="915" alt="Screenshot 2025-05-04 at 8 39 50 AM" src="https://github.com/user-attachments/assets/6c993c46-d96a-450e-94b0-41ca66d07b75" />

**Why This Works**
The key is the correlated subquery - it re-calculates for each row:

1.Takes the current row's age and power

2.Finds all wands with that same age and power

3.Returns the minimum coins_needed from that group

4.Only keeps rows where the current wand's coins_needed matches that minimum

5.This ensures we get exactly one wand (the cheapest) for each (age, power) combination.
