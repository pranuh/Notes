# Day 5: Joins Part 1

**Day 5 – Primary Key, Foreign Key, INNER JOIN, LEFT JOIN, RIGHT JOIN

---

# Story Before Learning Joins

Imagine you order food from Swiggy.

Swiggy does NOT store everything in one giant table.

Instead:

Customer details are stored separately.

Order details are stored separately.

Menu items are stored separately.

Restaurant details are stored separately.

Why?

- Avoid duplication
- Reduce storage
- Improve performance
- Maintain data consistency

This concept is called **Database Normalization**.

To get meaningful information, SQL combines tables using **JOINS**.

---

# Danny's Diner Database

We will use the following three tables.

---

# Table 1: Sales

Tracks what customers ordered.

| customer_id | order_date | product_id |
|------------|------------|------------|
| A | 2021-01-01 | 1 |
| A | 2021-01-01 | 2 |
| A | 2021-01-07 | 2 |
| A | 2021-01-10 | 3 |
| B | 2021-01-01 | 2 |
| B | 2021-01-04 | 1 |
| B | 2021-01-16 | 3 |
| C | 2021-01-01 | 3 |

---

# Table 2: Menu

Maps Product ID to Product Name.

| product_id | product_name | price |
|------------|-------------|--------|
| 1 | Sushi | 10 |
| 2 | Curry | 15 |
| 3 | Ramen | 12 |

---

# Table 3: Members

Tracks loyalty program members.

| customer_id | join_date |
|------------|-----------|
| A | 2021-01-07 |
| B | 2021-01-09 |

---

# Why Multiple Tables?

Without multiple tables:

| customer | item | price |
|----------|------|--------|
| A | Sushi | 10 |
| A | Sushi | 10 |
| A | Sushi | 10 |

Repeated values waste storage.

Instead:

Sales stores only Product IDs.

Menu stores product information once.

---

# Primary Key (PK)

## Simple Definition

A Primary Key uniquely identifies each row in a table.

Properties:

- Unique
- Cannot be NULL
- One primary key per table

---

# Example

Menu Table

| product_id | product_name |
|------------|-------------|
| 1 | Sushi |
| 2 | Curry |
| 3 | Ramen |

Here:

```text
product_id
```

is the Primary Key.

Because:

- No duplicates
- No NULL values

---

# Real-Life Example

## Aadhaar Number

```text
Person Name = Pranay
Aadhaar = 1234

Person Name = Rahul
Aadhaar = 5678
```

Aadhaar uniquely identifies a person.

Just like a Primary Key identifies a row.

---

# Foreign Key (FK)

## Simple Definition

A Foreign Key is a column that references a Primary Key in another table.

---

# Example

Sales Table

| customer_id | order_date | product_id |
|------------|------------|------------|
| A | 2021-01-01 | 1 |
| A | 2021-01-01 | 2 |

Menu Table

| product_id | product_name |
|------------|-------------|
| 1 | Sushi |
| 2 | Curry |

Here:

```text
Sales.product_id
```

references

```text
Menu.product_id
```

Therefore:

```text
Sales.product_id = Foreign Key
Menu.product_id  = Primary Key
```

---

# Relationship Diagram

```text
           MENU
+-----------------------+
| product_id (PK)       |
| product_name          |
| price                 |
+-----------------------+
          |
          |
          |
          V
         SALES
+-----------------------+
| customer_id           |
| order_date            |
| product_id (FK)       |
+-----------------------+
```

---

# What is a JOIN?

## Simple Definition

A JOIN combines rows from two or more tables using a related column.

---

# Visual Representation

```text
Table A           Table B

+------+          +------+
|  1   |          |  1   |
|  2   |          |  2   |
|  3   |          |  4   |
+------+          +------+
```

Common Value:

```text
1
2
```

JOIN connects matching values.

---

# INNER JOIN

## Simple Definition

Returns only matching records from both tables.

---

# Diagram

```text
     Table A
   +---------+
   |    A    |
   |  INNER  |
   |    B    |
   +---------+
     Table B

Only Common Records
```

---

# Example

Display ordered item names.

```sql
SELECT s.customer_id,
       m.product_name
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id;
```

---

# Result

| customer_id | product_name |
|------------|-------------|
| A | Sushi |
| A | Curry |
| B | Curry |
| C | Ramen |

---

# Business Question

What products did customers purchase?

Answer using INNER JOIN.

---

# LEFT JOIN

## Simple Definition

Returns:

- All records from LEFT table
- Matching records from RIGHT table

If no match exists:

NULL is returned.

---

# Diagram

```text
+-----------+
| LEFT JOIN |
+-----------+

All Left Records
+
Matching Right Records
```

---

# Example

Find all customers and membership details.

```sql
SELECT s.customer_id,
       mb.join_date
FROM Sales s
LEFT JOIN Members mb
ON s.customer_id = mb.customer_id;
```

---

# Result

| customer_id | join_date |
|------------|-----------|
| A | 2021-01-07 |
| B | 2021-01-09 |
| C | NULL |

Customer C is included because LEFT JOIN keeps all rows from Sales.

---

# Real-Life Story

College Students Table

| Student_ID |
|------------|
| 101 |
| 102 |
| 103 |

Scholarship Table

| Student_ID |
|------------|
| 101 |
| 102 |

LEFT JOIN shows:

```text
101 Scholarship
102 Scholarship
103 NULL
```

Student 103 still appears.

---

# RIGHT JOIN

## Simple Definition

Returns:

- All rows from RIGHT table
- Matching rows from LEFT table

---

# Diagram

```text
+------------+
| RIGHT JOIN |
+------------+

All Right Records
+
Matching Left Records
```

---

# Example

```sql
SELECT s.customer_id,
       mb.join_date
FROM Sales s
RIGHT JOIN Members mb
ON s.customer_id = mb.customer_id;
```

---

# INNER vs LEFT vs RIGHT

| JOIN Type | Returns |
|------------|----------|
| INNER JOIN | Only Matches |
| LEFT JOIN | All Left + Matches |
| RIGHT JOIN | All Right + Matches |

---

# Comparison Diagram

```text
INNER JOIN

     A
   (###)
     B

Only overlap


LEFT JOIN

Entire Left
+
Matching Right


RIGHT JOIN

Entire Right
+
Matching Left
```

---

# Alias in Joins

Without Alias

```sql
SELECT Sales.customer_id,
       Menu.product_name
FROM Sales
INNER JOIN Menu
ON Sales.product_id = Menu.product_id;
```

With Alias

```sql
SELECT s.customer_id,
       m.product_name
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id;
```

Preferred in industry.

---

# Common Interview Questions

Q1. Difference between Primary Key and Foreign Key?

| Primary Key | Foreign Key |
|-------------|------------|
| Unique | Can repeat |
| Cannot be NULL | Can contain NULL |
| Identifies row | References another table |

---

Q2. Difference between INNER and LEFT JOIN?

| INNER JOIN | LEFT JOIN |
|------------|-----------|
| Only matching records | All left records |
| Unmatched removed | Unmatched retained |

---

# Day 5 Summary

You should now be able to:

- Understand table relationships
- Identify Primary Keys
- Identify Foreign Keys
- Understand database normalization
- Write INNER JOIN queries
- Write LEFT JOIN queries
- Write RIGHT JOIN queries
- Use aliases in joins
- Explain joins using real-world examples

---

# Practice Workbook

## Section D – Short Answer Questions

1. What is a Primary Key?

2. What is a Foreign Key?

3. Why do databases use multiple tables?

4. What is a JOIN?

5. What does INNER JOIN return?

6. What does LEFT JOIN return?

7. What does RIGHT JOIN return?

8. What is the relationship between Sales and Menu tables?

9. Why are aliases used in JOIN queries?

10. What happens when no matching record exists in LEFT JOIN?

---

## Section F – Write SQL Queries

1. Display customer_id and product_name.

2. Display customer_id, product_name and price.

3. Display all sales records with menu details.

4. Display all customers and membership dates.

5. Display customers who joined the membership program.

6. Display customer purchases along with product prices.

7. Display customer_id and total amount spent.

8. Display all products purchased by customer A.

9. Display all purchases made before joining membership.

10. Display all customers including those without membership.

---

## Section G – Find the Error

### 1

```sql
SELECT *
FROM Sales
JOIN Menu;
```

### 2

```sql
SELECT *
FROM Sales s
INNER JOIN Menu m
s.product_id = m.product_id;
```

### 3

```sql
SELECT *
FROM Sales
LEFT Menu
ON Sales.product_id = Menu.product_id;
```

### 4

```sql
SELECT customer_id,
       product_name
FROM Sales
INNER JOIN Menu
ON product_id = product_id;
```

### 5

```sql
SELECT *
FROM Sales
RIGHT JOIN Members;
```

---
# Advanced JOIN Examples

## Example 1: Filter Records After Join

Display only purchases made by Customer A.

```sql
SELECT s.customer_id,
       m.product_name,
       m.price
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id
WHERE s.customer_id = 'A';
```

---

## Example 2: Multiple Filters

Display products purchased by Customer B costing more than 10.

```sql
SELECT s.customer_id,
       m.product_name,
       m.price
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id
WHERE s.customer_id = 'B'
AND m.price > 10;
```

---

## Example 3: Membership Customers Only

Display purchases made only by customers who joined membership.

```sql
SELECT s.customer_id,
       m.product_name
FROM Sales s
INNER JOIN Members mb
ON s.customer_id = mb.customer_id
INNER JOIN Menu m
ON s.product_id = m.product_id;
```

---

## Example 4: Customers Without Membership

```sql
SELECT s.customer_id
FROM Sales s
LEFT JOIN Members mb
ON s.customer_id = mb.customer_id
WHERE mb.customer_id IS NULL;
```

---

# JOIN + Aggregate Functions

## Example 5: Total Amount Spent By Each Customer

```sql
SELECT s.customer_id,
       SUM(m.price) AS Total_Spent
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id
GROUP BY s.customer_id;
```

---

## Example 6: Total Orders By Customer

```sql
SELECT customer_id,
       COUNT(*) AS Total_Orders
FROM Sales
GROUP BY customer_id;
```

---

## Example 7: Total Revenue By Product

```sql
SELECT m.product_name,
       SUM(m.price) AS Revenue
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id
GROUP BY m.product_name;
```

---

## Example 8: Most Popular Product

```sql
SELECT m.product_name,
       COUNT(*) AS Total_Orders
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id
GROUP BY m.product_name
ORDER BY Total_Orders DESC;
```

---

# JOIN + HAVING

## Example 9: Customers Spending More Than 30

```sql
SELECT s.customer_id,
       SUM(m.price) AS Total_Spent
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id
GROUP BY s.customer_id
HAVING SUM(m.price) > 30;
```

---

## Example 10: Products Ordered More Than 2 Times

```sql
SELECT m.product_name,
       COUNT(*) AS Total_Orders
FROM Sales s
INNER JOIN Menu m
ON s.product_id = m.product_id
GROUP BY m.product_name
HAVING COUNT(*) > 2;
```

---

# Real Interview Style Questions

1. Display customer names and purchased products.

2. Display all products purchased by Customer A.

3. Display customers who joined the loyalty program.

4. Display customers who never joined the loyalty program.

5. Find total amount spent by each customer.

6. Find total orders placed by each customer.

7. Find the most ordered product.

8. Find total revenue generated by each product.

9. Display customers who spent more than 30.

10. Display products ordered more than 2 times.

11. Find total sales for membership customers.

12. Find customers who purchased Ramen.

13. Find customers who purchased both Sushi and Curry.

14. Find products purchased after membership join date.

15. Find the first product purchased by each customer.
