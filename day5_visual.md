# Visual Understanding of SQL Joins

---

# Sample Tables

## Customers

| Customer_ID | Customer_Name |
|-------------|--------------|
| A | Alex |
| B | Bob |
| C | Charlie |

---

## Members

| Customer_ID | Join_Date |
|-------------|------------|
| A | 2021-01-07 |
| B | 2021-01-09 |
| D | 2021-01-20 |

---

# INNER JOIN

Returns only matching records from both tables.

## Venn Diagram

```text
Customers                Members

     ◯──────────◯
   ◯      AB      ◯
     ◯──────────◯

Only the intersection is returned.
```

## Result

| Customer_ID |
|-------------|
| A |
| B |

---

# LEFT JOIN

Returns:

- All rows from LEFT table
- Matching rows from RIGHT table

## Venn Diagram

```text
Customers                Members

[ A B C ]    +    [ A B D ]

Result:

A
B
C
```

Visual:

```text
   LEFT TABLE

 ┌──────────────┐
 │ A            │
 │ B            │
 │ C            │
 └──────────────┘

      JOIN

 ┌──────────────┐
 │ A            │
 │ B            │
 │ D            │
 └──────────────┘

OUTPUT:

A
B
C
```

## Result

| Customer_ID | Join_Date |
|-------------|------------|
| A | 2021-01-07 |
| B | 2021-01-09 |
| C | NULL |

---

# RIGHT JOIN

Returns:

- All rows from RIGHT table
- Matching rows from LEFT table

## Diagram

```text
Customers                Members

[ A B C ]    +    [ A B D ]

Result:

A
B
D
```

## Result

| Customer_ID | Join_Date |
|-------------|------------|
| A | 2021-01-07 |
| B | 2021-01-09 |
| D | 2021-01-20 |

---

# Join Memory Trick

```text
INNER JOIN

Only Common Records

LEFT JOIN

Everything from LEFT
+
Matching from RIGHT

RIGHT JOIN

Everything from RIGHT
+
Matching from LEFT
```

---

# Visual Row Matching

Customers

| Customer_ID |
|-------------|
| A |
| B |
| C |

Members

| Customer_ID |
|-------------|
| A |
| B |
| D |

Matching Process

A = Match ✅

B = Match ✅

C = No Match ❌

D = No Match ❌

INNER JOIN Result

A
B

LEFT JOIN Result

A
B
C

RIGHT JOIN Result

A
B
D

---

# Quick Comparison

| Join Type | Returns |
|------------|----------|
| INNER JOIN | Only matching rows |
| LEFT JOIN | All left rows + matching right rows |
| RIGHT JOIN | All right rows + matching left rows |

---

# Interview Shortcut

```text
INNER = Common

LEFT = Keep Left

RIGHT = Keep Right
```