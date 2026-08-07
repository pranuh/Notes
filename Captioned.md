# SQL Capstone Project & Placement Assessment

**Syllabus Mapping:** Revision & Practical Application (Comprehensive Review)

> **Note:** This capstone consolidates concepts from **Day 1 to Day 8** and is intended as a revision, assessment, and placement preparation activity using the **IPL 2026 Dataset**.

---

# Learning Outcomes

By completing this capstone project, students will be able to:

- Apply SQL concepts to solve real-world business problems.
- Write optimized SQL queries using multiple techniques.
- Combine Joins, Grouping, Aggregate Functions, and Subqueries.
- Improve analytical and logical thinking.
- Prepare for SQL coding rounds and technical interviews.

---

# Dataset Used

The following IPL tables will be used throughout the assessment.

## Table 1 : squads

```text
team_no
team_name
player
nationality
role
designation
```

---

## Table 2 : batting_stats

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
fours
sixes
```

---

## Table 3 : bowling_stats

```text
position
bowler
team
matches
innings
wickets
economy
overs
avg
```

---

## Table 4 : points_table

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

# Part 1 – IPL Analytics Case Study

Assume you are working as a **Data Analyst for the IPL Governing Council**.

The management requires various analytical reports to evaluate team and player performances.

Your task is to answer the following business questions using SQL.

---

# Case Study 1 – Team Performance

### Easy

1. Display the Top 4 qualified teams.

2. Find the team with the highest Net Run Rate (NRR).

3. Display the team with the maximum number of wins.

4. Display all teams having a positive NRR.

### Medium

5. Find teams having more than 16 points.

6. Display teams whose wins are above the league average.

7. Display teams with an NRR above the average NRR.

8. Display teams that qualified for playoffs but have fewer than 9 wins.

### Advanced

9. Find teams that do not have an overseas wicketkeeper.

10. Find teams where every player is an Indian player.

---

# Case Study 2 – Batting Analysis

### Easy

1. Display the Orange Cap holder.

2. Find the Top 10 run scorers.

3. Display all century scorers.

4. Display players having more than 500 runs.

### Medium

5. Display batsmen scoring above the league average runs.

6. Display batsmen scoring above their team average.

7. Display the Top 5 players by strike rate.

8. Find players who have scored more than 50 fours.

### Advanced

9. Display players having no fifties.

10. Find batsmen whose strike rate is higher than every batsman in their team.

11. Find teams having more than three batsmen scoring above 400 runs.

12. Display batsmen whose average is above the league average but strike rate is below the league average.

---

# Case Study 3 – Bowling Analysis

### Easy

1. Display the Purple Cap holder.

2. Find bowlers with more than 20 wickets.

3. Display the Top 10 wicket takers.

### Medium

4. Display bowlers with economy below the league average.

5. Display bowlers taking more wickets than their team average.

6. Display bowlers having economy below 8.

### Advanced

7. Find teams without a 15+ wicket bowler.

8. Find bowlers whose economy is better than every bowler in their team.

9. Display teams having more than two bowlers with 15+ wickets.

10. Find bowlers whose wickets are above league average but economy is below league average.

---

# Case Study 4 – Combined Reports

Students must solve these questions using a combination of:

- JOIN
- GROUP BY
- HAVING
- Aggregate Functions
- Subqueries
- EXISTS / NOT EXISTS
- ANY / ALL

---

## Business Questions

1. Which playoff teams have more than three batsmen scoring 400+ runs?

2. Which teams have both a 500+ run scorer and a 15+ wicket bowler?

3. Which teams have an above-average NRR but below-average batting performance?

4. Which teams have more overseas players than Indian players?

5. Which teams have the highest average batting strike rate?

6. Which teams have the lowest bowling economy?

7. Find teams where no batsman has scored a century.

8. Find teams having at least one batsman and one bowler in the Top 10 rankings.

9. Which teams have more than two all-rounders?

10. Display teams whose average batting performance is higher than average bowling performance.

---

# Part 2 – SQL Challenge Set

Questions are arranged in increasing order of difficulty.

---

# Level 1 – Easy (10 Questions)

1. Display all teams.

2. Display all batsmen sorted by runs.

3. Display bowlers sorted by wickets.

4. Display all Indian players.

5. Display overseas players.

6. Find players with more than 500 runs.

7. Find bowlers with economy below 8.

8. Display Top 5 run scorers.

9. Display Top 5 wicket takers.

10. Display teams with positive NRR.

---

# Level 2 – Medium (10 Questions)

1. Count players in each team.

2. Count overseas players in each team.

3. Display average runs team-wise.

4. Display average wickets team-wise.

5. Display maximum strike rate per team.

6. Display minimum economy per team.

7. Find teams having more than 20 players.

8. Display teams with average batting above league average.

9. Display teams with more than one wicketkeeper.

10. Display teams having more than three overseas players.

---

# Level 3 – Advanced (10 Questions)

1. Players above league average runs.

2. Bowlers above league average wickets.

3. Players above team average runs.

4. Bowlers above team average wickets.

5. Teams with positive NRR using EXISTS.

6. Teams without overseas players using NOT EXISTS.

7. Players scoring above ANY CSK batsman.

8. Players scoring above ALL MI batsmen.

9. Teams with more wins than average.

10. Teams with more points than playoff average.

---

# Level 4 – Expert (10 Questions)

1. Find the team of the Orange Cap holder.

2. Find the team of the Purple Cap holder.

3. Display teams with both Orange and Purple Cap contenders.

4. Find teams whose batting average exceeds bowling average.

5. Find teams having more than three players with 500+ runs.

6. Find teams having multiple bowlers with 15+ wickets.

7. Display teams qualifying through positive NRR despite fewer wins.

8. Find batsmen outperforming every teammate.

9. Find bowlers outperforming every teammate.

10. Build a complete team performance summary using JOIN, GROUP BY, HAVING, and Subqueries.

---

# Part 3 – SQL Debugging Round

Students must identify and correct the errors.

The questions cover:

- Incorrect JOIN conditions
- Missing GROUP BY columns
- Incorrect HAVING usage
- WHERE vs HAVING confusion
- EXISTS syntax errors
- Correlated Subquery mistakes
- Aggregate function misuse
- Missing aliases
- Incorrect IN syntax
- ANY / ALL syntax errors
- Incorrect NULL handling
- ORDER BY mistakes
- Nested Subquery mistakes
- JOIN duplication issues
- GROUP BY with Aggregate errors

---

# Part 4 – Placement Mock Test

**Duration:** 60 Minutes

---

## Section A

### MCQs (15 × 1 = 15 Marks)

Topics covered:

- SQL Fundamentals
- Operators
- Functions
- GROUP BY
- HAVING
- Joins
- Subqueries
- EXISTS
- ANY
- ALL

---

## Section B

### Output Prediction (10 × 2 = 20 Marks)

Students predict the output of SQL queries.

Topics include:

- Aggregate Functions
- Joins
- GROUP BY
- Subqueries
- ORDER BY
- DISTINCT

---

## Section C

### SQL Query Writing (10 × 4 = 40 Marks)

Students solve business scenarios using SQL.

Difficulty ranges from beginner to advanced.

---

## Section D

### SQL Debugging (5 × 5 = 25 Marks)

Students identify and correct SQL errors.

---

# Part 5 – Mock Interview Round

Students should be able to confidently answer the following interview questions.

1. Explain SQL Query Execution Order.

2. Difference between WHERE and HAVING.

3. Difference between JOIN and Subquery.

4. Difference between EXISTS and IN.

5. Difference between ANY and ALL.

6. Difference between LEFT JOIN and RIGHT JOIN.

7. Difference between COUNT(*) and COUNT(column).

8. Why are Correlated Subqueries slower?

9. Difference between Aggregate Functions and Single Row Functions.

10. Explain a real-world use case of GROUP BY.

11. What is the difference between Primary Key and Foreign Key?

12. Explain INNER JOIN using an example.

13. What happens when GROUP BY is omitted?

14. What is the difference between DISTINCT and GROUP BY?

15. How can SQL queries be optimized?

---

# Part 6 – Mini Project

# IPL Tournament Analytics Dashboard

Students will develop SQL queries to generate an IPL dashboard containing the following reports.

### Team Reports

- Team Rankings
- Playoff Teams
- Team-wise Performance Summary
- Team Win Percentage
- Positive NRR Teams

---

### Batting Reports

- Top 10 Batsmen
- Orange Cap Holder
- Highest Strike Rate
- Most Fours
- Most Sixes
- Century Scorers
- Fifty Scorers

---

### Bowling Reports

- Top 10 Bowlers
- Purple Cap Holder
- Best Economy
- Most Wickets
- Best Bowling Average

---

### Player Reports

- Overseas Player Report
- Indian Player Report
- Wicketkeepers
- All-rounders
- Team-wise Player Distribution

---

### Comparative Reports

- Batting vs Bowling Comparison
- Team Batting Strength
- Team Bowling Strength
- Best Balanced Team
- Team Performance Dashboard

---

# Final Learning Outcome

By completing this capstone project, students will have practiced:

- SELECT
- WHERE
- ORDER BY
- GROUP BY
- HAVING
- Aggregate Functions
- Joins
- Single Row Functions
- Subqueries
- Correlated Subqueries
- Nested Queries
- EXISTS
- NOT EXISTS
- IN
- ANY
- ALL

Students completing this capstone should be well-prepared for SQL coding rounds, university practical examinations, and entry-level technical interviews.
