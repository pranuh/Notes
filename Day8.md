# Day 8: Advanced SQL Operators 

---

# Dataset Used

## Table 1: squads

```text
team_no
team_name
player
nationality
role
designation
```

---

## Table 2: batting_stats

```text
position
batsman
team
matches
innings
runs
average
strike_rate
high_score
hundreds
fifties
```

---

## Table 3: bowling_stats

```text
position
bowler
team
matches
wickets
economy
avg
```

---

## Table 4: points_table

```text
position
team
matches
wins
losses
points
nrr
```

---

# Part 1 – Student Notes

# Day 7 Quick Revision

Yesterday we learned

- Single Row Subqueries
- Multiple Row Subqueries
- Correlated Subqueries
- Nested Queries

Today we will learn advanced operators that work with subqueries.

---

# Story

Imagine IPL Management asks:

- Show players from playoff teams.
- Show teams that have at least one batsman with 700+ runs.
- Show teams that have no foreign wicketkeeper.
- Show batsmen scoring more than every batsman in CSK.

These questions require advanced SQL operators.

---

# 1. IN Operator

## Definition

IN checks whether a value exists in a list returned by a subquery.

---

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name IN
(
    SELECT column_name
    FROM another_table
);
```

---

## Example 1

Find players from Top 4 teams.

```sql
SELECT player,
       team_name
FROM squads
WHERE team_name IN
(
    SELECT team
    FROM points_table
    WHERE position <= 4
);
```

---

## Example 2

Find bowlers from teams having more than 16 points.

```sql
SELECT bowler
FROM bowling_stats
WHERE team IN
(
    SELECT team
    FROM points_table
    WHERE points > 16
);
```

---

## Example 3

Find batsmen from teams with positive NRR.

```sql
SELECT batsman
FROM batting_stats
WHERE team IN
(
    SELECT team
    FROM points_table
    WHERE nrr > 0
);
```

---

## Important Points

- Used with multiple values
- Replaces multiple OR conditions
- Improves readability

---

# 2. EXISTS Operator

## Definition

EXISTS checks whether the subquery returns at least one row.

If rows exist → TRUE

Otherwise → FALSE

---

## Story

Management asks

"Show teams that have at least one batsman scoring above 600 runs."

We only need to know whether such a player exists.

---

## Syntax

```sql
SELECT *
FROM table1 t1
WHERE EXISTS
(
    SELECT *
    FROM table2 t2
    WHERE ...
);
```

---

## Example 1

Find teams having at least one batsman with 600+ runs.

```sql
SELECT team
FROM points_table p
WHERE EXISTS
(
    SELECT *
    FROM batting_stats b
    WHERE b.team = p.team
    AND runs > 600
);
```

---

## Example 2

Find teams having bowlers with more than 20 wickets.

```sql
SELECT team
FROM points_table p
WHERE EXISTS
(
    SELECT *
    FROM bowling_stats b
    WHERE b.team = p.team
    AND wickets > 20
);
```

---

## Why EXISTS?

- Stops searching after finding the first matching row
- Efficient for large datasets
- Common in interviews

---

# 3. NOT EXISTS

## Definition

Returns rows where the subquery finds no matching records.

---

## Story

Management asks

"Show teams without any foreign players."

---

## Example 1

```sql
SELECT team
FROM points_table p
WHERE NOT EXISTS
(
    SELECT *
    FROM squads s
    WHERE s.team_name = p.team
    AND nationality <> 'India'
);
```

---

## Example 2

Find teams without any batsman scoring 500 runs.

```sql
SELECT team
FROM points_table p
WHERE NOT EXISTS
(
    SELECT *
    FROM batting_stats b
    WHERE b.team = p.team
    AND runs >= 500
);
```

---

## Example 3

Find teams without bowlers taking more than 15 wickets.

```sql
SELECT team
FROM points_table p
WHERE NOT EXISTS
(
    SELECT *
    FROM bowling_stats b
    WHERE b.team = p.team
    AND wickets > 15
);
```

---

# EXISTS vs NOT EXISTS

| EXISTS | NOT EXISTS |
|---------|------------|
| Matching rows exist | No matching rows exist |
| TRUE if found | TRUE if not found |
| Common for validations | Common for missing data |

---

# 4. ANY Operator

## Definition

ANY compares a value with any value returned by the subquery.

Condition becomes TRUE if at least one comparison succeeds.

---

## Syntax

```sql
SELECT ...
FROM table
WHERE value > ANY
(
    SELECT ...
);
```

---

## Example 1

Find batsmen scoring more runs than at least one CSK batsman.

```sql
SELECT batsman,
       runs
FROM batting_stats
WHERE runs >
ANY
(
    SELECT runs
    FROM batting_stats
    WHERE team='CSK'
);
```

---

## Example 2

Find bowlers with more wickets than any MI bowler.

```sql
SELECT bowler
FROM bowling_stats
WHERE wickets >
ANY
(
    SELECT wickets
    FROM bowling_stats
    WHERE team='MI'
);
```

---

## Important Note

ANY behaves like

```text
Greater than at least one value
```

---

# 5. ALL Operator

## Definition

ALL compares a value with every value returned by the subquery.

Condition becomes TRUE only if all comparisons succeed.

---

## Example 1

Find batsmen scoring more runs than every CSK batsman.

```sql
SELECT batsman,
       runs
FROM batting_stats
WHERE runs >
ALL
(
    SELECT runs
    FROM batting_stats
    WHERE team='CSK'
);
```

---

## Example 2

Find bowlers having better economy than every MI bowler.

```sql
SELECT bowler
FROM bowling_stats
WHERE economy <
ALL
(
    SELECT economy
    FROM bowling_stats
    WHERE team='MI'
);
```

---

# ANY vs ALL

Suppose CSK batsmen scored

```text
420
480
520
690
```

Condition

```text
Runs > ANY
```

Means

```text
Greater than at least one value
```

Example

```text
500 ✔
```

Condition

```text
Runs > ALL
```

Means

```text
Greater than every value
```

Example

```text
700 ✔
```

---

# IN vs EXISTS

| IN | EXISTS |
|----|---------|
| Compares values | Checks row existence |
| Returns matching values | Returns TRUE/FALSE |
| Good for small lists | Better for large tables |

---

# SQL Execution Order

```text
FROM

WHERE

GROUP BY

HAVING

SELECT

ORDER BY
```

---

# Common Interview Questions

### Q1

Difference between IN and EXISTS?

---

### Q2

Difference between EXISTS and NOT EXISTS?

---

### Q3

Difference between ANY and ALL?

---

### Q4

When should EXISTS be preferred?

---

### Q5

Why is EXISTS faster than IN in some cases?

---

### Q6

Difference between JOIN and EXISTS?

---

### Q7

Difference between NOT IN and NOT EXISTS?

---

### Q8

Can EXISTS return values?

---

### Q9

Can ANY work without a subquery?

---

### Q10

Which operator performs better on large tables?

---

# Day 8 Summary

You should now be able to

✔ Use IN

✔ Use EXISTS

✔ Use NOT EXISTS

✔ Use ANY

✔ Use ALL

✔ Compare advanced SQL operators

✔ Solve interview questions

✔ Complete SQL assessments

---

# Part 2 – Practice Workbook

## Section D – Short Answer Questions

1. What is the purpose of IN?

2. What does EXISTS check?

3. What does NOT EXISTS return?

4. Difference between ANY and ALL.

5. Difference between IN and EXISTS.

6. Can EXISTS return column values?

7. Why is EXISTS faster on large datasets?

8. What is the purpose of ALL?

9. When should NOT EXISTS be used?

10. Give one real-world use case of ANY.

---

# Section E – Multiple Choice Questions

1. Which operator checks whether at least one matching row exists?

A. IN

B. EXISTS

C. ANY

D. ALL

---

2. Which operator is generally more efficient for large correlated searches?

A. IN

B. EXISTS

C. DISTINCT

D. LIKE

---

3. Which operator compares with every value returned by a subquery?

A. ANY

B. EXISTS

C. ALL

D. BETWEEN

---

4. Which operator returns TRUE when no matching rows exist?

A. EXISTS

B. NOT EXISTS

C. IN

D. ALL

---

5. Which operator replaces multiple OR conditions?

A. IN

B. ALL

C. EXISTS

D. ANY

---

# Section F – Write SQL Queries

### IN

1. Find players from Top 4 teams.

2. Find bowlers from teams having more than 14 points.

3. Find batsmen from teams with positive NRR.

4. Find Indian players from playoff teams.

5. Find all-rounders from teams with more than 8 wins.

### EXISTS

6. Find teams having at least one batsman with 600+ runs.

7. Find teams having bowlers with more than 20 wickets.

8. Find teams having at least one overseas player.

9. Find teams having a wicketkeeper.

10. Find teams having at least one century scorer.

### NOT EXISTS

11. Find teams without overseas players.

12. Find teams without century scorers.

13. Find teams without bowlers taking 15 wickets.

14. Find teams without wicketkeepers.

15. Find teams without players averaging above 50.

### ANY

16. Find batsmen scoring more than any MI batsman.

17. Find bowlers taking more wickets than any RCB bowler.

18. Find players earning more than any overseas player (if salary data exists).

19. Find batsmen with strike rates higher than any CSK batsman.

20. Find bowlers with economy better than any KKR bowler.

### ALL

21. Find batsmen scoring more than every CSK batsman.

22. Find bowlers taking more wickets than every MI bowler.

23. Find players averaging higher than every SRH batsman.

24. Find bowlers with economy lower than every DC bowler.

25. Find players with more sixes than every PBKS batsman.

---

# Section G – Debug the SQL

1.

```sql
SELECT *
FROM squads
WHERE team_name IN
SELECT team
FROM points_table;
```

2.

```sql
SELECT *
FROM points_table
WHERE EXISTS
(
runs > 500
);
```

3.

```sql
SELECT *
FROM batting_stats
WHERE runs >
ALL
SELECT runs
FROM batting_stats;
```

4.

```sql
SELECT *
FROM bowling_stats
WHERE wickets >
ANY
(
SELECT *
FROM bowling_stats
);
```

5.

```sql
SELECT *
FROM squads
WHERE NOT EXIST
(
SELECT *
FROM batting_stats
);
```

---

# Section H – Mini Mock Placement Test (25 Marks)

### Part A – Theory (5 × 1 = 5 Marks)

1. Define EXISTS.
2. Difference between ANY and ALL.
3. Why is IN preferred over OR?
4. What does NOT EXISTS return?
5. Give one use case of EXISTS.

### Part B – SQL Queries (5 × 3 = 15 Marks)

1. Find players from Top 4 teams.

2. Find batsmen with runs greater than league average.

3. Find bowlers from teams having positive NRR.

4. Find teams having at least one century scorer.

5. Find batsmen scoring more than every MI batsman.
