# Subqueries in SQL using IPL 2026 Dataset

- Single Row Subqueries
- Multiple Row Subqueries
- Correlated Subqueries
- Nested Queries

### Learning Outcome

By the end of this session, students will be able to:

- Write subqueries inside SELECT statements
- Retrieve data using Single Row Subqueries
- Retrieve data using Multiple Row Subqueries
- Solve business problems using Correlated Subqueries
- Build Nested Queries
- Solve interview-oriented SQL questions

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

### Sample Data

| Team | Player | Role |
|--------|--------|--------|
| RCB | Virat Kohli | Batsman |
| RCB | Rajat Patidar | Batsman |
| MI | Rohit Sharma | Batsman |
| MI | Hardik Pandya | All-Rounder |
| CSK | MS Dhoni | WK-Batsman |
| CSK | Ravindra Jadeja | All-Rounder |

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
fifties
hundreds
fours
sixes
```

---

## Table 3: bowling_stats

```text
position
bowler
team
matches
innings
wickets
economy
overs
runs
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

# Quick Revision

Previously we learned:

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL OUTER JOIN
- SELF JOIN
- CROSS JOIN
- Multiple Table Joins

Today we will learn:

```text
Query inside Query
```

This concept is called a Subquery.

---

# Story Time

Imagine IPL management asks:

> "Show me the batsman who scored the most runs."

Can we manually check all rows?

No.

Instead:

Step 1

Find Maximum Runs.

Step 2

Find the player who scored those runs.

This is exactly what a Subquery does.

---

# What is a Subquery?

## Definition

A query written inside another query is called a Subquery.

---

## General Structure

```sql
SELECT column_name
FROM table_name
WHERE column_name =
(
    SELECT ...
);
```

---

# Why Use Subqueries?

Subqueries help us:

- Compare against maximum values
- Compare against minimum values
- Compare against averages
- Retrieve related records
- Build advanced reports

---

# Types of Subqueries

1. Single Row Subquery
2. Multiple Row Subquery
3. Correlated Subquery
4. Nested Query

---

# 1. Single Row Subquery

## Definition

Returns exactly one value.

Usually used with:

```text
=
>
<
>=
<=
<>
```

---

# Example 1

Find the batsman with maximum runs.

```sql
SELECT batsman,
       runs
FROM batting_stats
WHERE runs =
(
    SELECT MAX(runs)
    FROM batting_stats
);
```

---

# Example 2

Find bowler with maximum wickets.

```sql
SELECT bowler,
       wickets
FROM bowling_stats
WHERE wickets =
(
    SELECT MAX(wickets)
    FROM bowling_stats
);
```

---

# Example 3

Find team with highest points.

```sql
SELECT team
FROM points_table
WHERE points =
(
    SELECT MAX(points)
    FROM points_table
);
```

---

# Example 4

Find batsmen scoring above average runs.

```sql
SELECT batsman,
       runs
FROM batting_stats
WHERE runs >
(
    SELECT AVG(runs)
    FROM batting_stats
);
```

---

# Example 5

Find bowlers having economy better than average.

```sql
SELECT bowler,
       economy
FROM bowling_stats
WHERE economy <
(
    SELECT AVG(economy)
    FROM bowling_stats
);
```

---

# Important Note

Single Row Subqueries return:

```text
One Value Only
```

Example:

```sql
SELECT MAX(runs)
FROM batting_stats;
```

Output:

```text
759
```

Only one value returned.

---

# 2. Multiple Row Subquery

## Definition

Returns multiple values.

Used with:

```text
IN
NOT IN
ANY
ALL
```

---

# Example 1

Find players from Top 4 teams.

```sql
SELECT player
FROM squads
WHERE team_name IN
(
    SELECT team
    FROM points_table
    WHERE position <= 4
);
```

---

# Example 2

Find bowlers from playoff teams.

```sql
SELECT bowler
FROM bowling_stats
WHERE team IN
(
    SELECT team
    FROM points_table
    WHERE position <= 4
);
```

---

# Example 3

Find players from teams with positive NRR.

```sql
SELECT player
FROM squads
WHERE team_name IN
(
    SELECT team
    FROM points_table
    WHERE nrr > 0
);
```

---

# Example 4

Find players who are not from bottom 2 teams.

```sql
SELECT player
FROM squads
WHERE team_name NOT IN
(
    SELECT team
    FROM points_table
    WHERE position >= 9
);
```

---

# IN vs =

Single Value

```sql
WHERE runs =
(
   SELECT MAX(runs)
   FROM batting_stats
);
```

Multiple Values

```sql
WHERE team IN
(
   SELECT team
   FROM points_table
);
```

---

# 3. Correlated Subquery

## Definition

The inner query depends on the outer query.

The inner query executes once for every row.

---

# Real-Life Example

Teacher says:

> Compare every student's marks with the average marks of THEIR class.

Different class.

Different average.

Same concept.

---

# Example 1

Find batsmen scoring above their team average.

```sql
SELECT b1.batsman,
       b1.team,
       b1.runs
FROM batting_stats b1
WHERE b1.runs >
(
    SELECT AVG(b2.runs)
    FROM batting_stats b2
    WHERE b1.team = b2.team
);
```

---

# Example 2

Find bowlers taking more wickets than their team average.

```sql
SELECT b1.bowler,
       b1.team,
       b1.wickets
FROM bowling_stats b1
WHERE b1.wickets >
(
    SELECT AVG(b2.wickets)
    FROM bowling_stats b2
    WHERE b1.team = b2.team
);
```

---

# Example 3

Find batsmen whose strike rate is above their team average.

```sql
SELECT batsman,
       team,
       strike_rate
FROM batting_stats b1
WHERE strike_rate >
(
    SELECT AVG(strike_rate)
    FROM batting_stats b2
    WHERE b1.team = b2.team
);
```

---

# Why Correlated Subqueries Are Slower

Normal Query

```text
Runs Once
```

Correlated Query

```text
Runs Once For Every Row
```

Hence slower.

---

# 4. Nested Queries

## Definition

Query inside Query inside Query.

---

# Example 1

Find players from the team with maximum points.

```sql
SELECT player
FROM squads
WHERE team_name =
(
    SELECT team
    FROM points_table
    WHERE points =
    (
        SELECT MAX(points)
        FROM points_table
    )
);
```

---

# Example 2

Find bowlers from the team with highest NRR.

```sql
SELECT bowler
FROM bowling_stats
WHERE team =
(
    SELECT team
    FROM points_table
    WHERE nrr =
    (
        SELECT MAX(nrr)
        FROM points_table
    )
);
```

---

# Example 3

Find players from the team of highest run scorer.

```sql
SELECT player
FROM squads
WHERE team_name =
(
    SELECT team
    FROM batting_stats
    WHERE runs =
    (
        SELECT MAX(runs)
        FROM batting_stats
    )
);
```

---

# Example 4

Find bowlers from team having maximum wins.

```sql
SELECT bowler
FROM bowling_stats
WHERE team =
(
    SELECT team
    FROM points_table
    WHERE wins =
    (
        SELECT MAX(wins)
        FROM points_table
    )
);
```

---

# Interview Corner

## Difference Between Single and Multiple Row Subquery

| Single Row | Multiple Row |
|------------|------------|
| One value | Many values |
| = | IN |
| MAX, MIN, AVG | IN, ANY, ALL |

---

## Difference Between Normal and Correlated Subquery

| Normal | Correlated |
|----------|----------|
| Runs once | Runs per row |
| Faster | Slower |
| Independent | Dependent |


---

# Part 2 – Practice Workbook

## Section – Short Answer Questions

1. What is a Subquery?

2. What is a Single Row Subquery?

3. What is a Multiple Row Subquery?

4. What is a Correlated Subquery?

5. What is a Nested Query?

6. Why do we use IN with Multiple Row Subqueries?

7. Why are Correlated Subqueries slower?

8. Can a Subquery return multiple values?

9. What is the difference between = and IN?

10. Can a Nested Query contain multiple levels?

---

## Section – Write SQL Queries

### Easy

1. Find batsman with maximum runs.

2. Find bowler with maximum wickets.

3. Find team with highest points.

4. Find batsman with minimum runs.

5. Find bowlers with economy below average.

### Medium

6. Find batsmen scoring above average runs.

7. Find bowlers taking above average wickets.

8. Find players from Top 4 teams.

9. Find players from teams with positive NRR.

10. Find players from teams having more than 8 wins.

### Correlated

11. Find batsmen scoring above team average.

12. Find bowlers taking more wickets than team average.

13. Find batsmen with strike rate above team average.

14. Find bowlers with economy better than team average.

15. Find players from teams whose average runs exceed overall average.

### Nested Queries

16. Find players from team with maximum points.

17. Find players from team with highest NRR.

18. Find bowlers from team with maximum wins.

19. Find players from team of highest run scorer.

20. Find bowlers from team of highest wicket taker.

---

## Section – Challenge Questions

1. Find players from teams whose points are above league average.

2. Find batsmen whose runs are greater than the highest run scorer of CSK.

3. Find bowlers whose wickets are higher than the average wickets of playoff teams.

4. Find teams having more batsmen above 500 runs than the league average.

5. Find players belonging to teams with both positive NRR and more than 7 wins.

---

# End of Day 7 Notes and Workbook
