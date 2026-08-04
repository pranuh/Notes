# SQL Joins 

- Primary Key
- Foreign Key
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL OUTER JOIN
- SELF JOIN
- CROSS JOIN
- Multiple Table Joins
- Real-Time Scenarios

---

# Learning Outcomes

By the end of this module, 
- Identify Primary Keys and Foreign Keys
- Understand table relationships
- Write INNER JOIN queries
- Write LEFT JOIN queries
- Write RIGHT JOIN queries
- Write FULL OUTER JOIN queries
- Write SELF JOIN queries
- Write CROSS JOIN queries
- Join multiple tables together
- Solve real-world reporting problems
- Use JOIN with GROUP BY and HAVING

---

# Business Story

Imagine you are working for Amazon.

Data is stored across multiple tables:

- Customers
- Orders
- Products
- Memberships
- Employees

A manager asks:

- Which customer spent the most?
- Which product generated the highest revenue?
- Which customers are Prime members?
- Which customers never purchased membership?
- Who reports to whom?
- Generate product bundle combinations.

These questions require JOINS.

---

# Database Relationship Diagram

```text
Customers
    |
    | Customer_ID
    |
Orders
    |
    | Product_ID
    |
Products

Customers
    |
    | Customer_ID
    |
Memberships

Employees
    |
    | Manager_ID
    |
Employees
```

---

# Sample Dataset

## Customers

| Customer_ID | Customer_Name | City |
|------------|---------------|------|
| C101 | Pranay | Hyderabad |
| C102 | Rahul | Bangalore |
| C103 | Sneha | Chennai |
| C104 | Kiran | Pune |
| C105 | Divya | Mumbai |
| C106 | Arjun | Delhi |
| C107 | Megha | Kolkata |
| C108 | Varun | Hyderabad |
| C109 | Rakesh | Chennai |
| C110 | Anjali | Bangalore |
| C111 | Teja | Pune |
| C112 | Nikhil | Mumbai |
| C113 | Lavanya | Delhi |
| C114 | Akhil | Hyderabad |
| C115 | Pooja | Chennai |

---

## Products

| Product_ID | Product_Name | Category | Price |
|------------|--------------|----------|-------|
| P1 | Laptop | Electronics | 60000 |
| P2 | Headphones | Electronics | 3000 |
| P3 | Office Chair | Furniture | 8000 |
| P4 | Smart Watch | Electronics | 5000 |
| P5 | Study Table | Furniture | 12000 |
| P6 | Keyboard | Electronics | 1500 |
| P7 | Mouse | Electronics | 800 |
| P8 | Monitor | Electronics | 15000 |
| P9 | Bookshelf | Furniture | 9000 |
| P10 | Printer | Electronics | 10000 |

---

## Memberships

| Customer_ID | Membership_Type |
|------------|-----------------|
| C101 | Prime |
| C102 | Prime |
| C104 | Gold |
| C106 | Prime |
| C108 | Gold |
| C110 | Prime |
| C112 | Gold |
| C120 | Prime |

---

## Employees

| Employee_ID | Employee_Name | Manager_ID |
|------------|---------------|------------|
| 1 | Amit | NULL |
| 2 | Neha | 1 |
| 3 | Raj | 1 |
| 4 | Priya | 2 |
| 5 | Karan | 2 |
| 6 | Rohit | 3 |
| 7 | Anita | 3 |
| 8 | Vijay | 4 |
| 9 | Sonia | 4 |
| 10 | Harish | 5 |

---

# PRIMARY KEY

## Definition

A Primary Key uniquely identifies each row.

### Example

```text
Customers
----------
Customer_ID
```

```text
Products
----------
Product_ID
```

```text
Orders
----------
Order_ID
```

---

# FOREIGN KEY

## Definition

A Foreign Key references a Primary Key from another table.

### Example

```text
Orders.Customer_ID
       |
       |
       V
Customers.Customer_ID
```

---

# INNER JOIN

## Definition

Returns only matching rows.

### Diagram

```text
Customers      Orders

   ( A )
     X
   ( B )

Only Matching Records
```

### Example

```sql
SELECT c.Customer_Name,
       o.Order_ID
FROM Customers c
INNER JOIN Orders o
ON c.Customer_ID = o.Customer_ID;
```

---

# LEFT JOIN

## Definition

Returns all rows from the left table.

### Example

```sql
SELECT c.Customer_Name,
       m.Membership_Type
FROM Customers c
LEFT JOIN Memberships m
ON c.Customer_ID = m.Customer_ID;
```

---

# RIGHT JOIN

## Definition

Returns all rows from the right table.

### Example

```sql
SELECT c.Customer_Name,
       m.Membership_Type
FROM Customers c
RIGHT JOIN Memberships m
ON c.Customer_ID = m.Customer_ID;
```

---

# FULL OUTER JOIN

## Definition

Returns all rows from both tables.

### Example

```sql
SELECT c.Customer_ID,
       m.Customer_ID
FROM Customers c
FULL OUTER JOIN Memberships m
ON c.Customer_ID = m.Customer_ID;
```

---

# SELF JOIN

## Definition

A table joined with itself.

### Example

```sql
SELECT e.Employee_Name,
       m.Employee_Name AS Manager
FROM Employees e
LEFT JOIN Employees m
ON e.Manager_ID = m.Employee_ID;
```

---

# CROSS JOIN

## Definition

Returns every possible combination.

### Formula

```text
Rows A × Rows B
```

### Example

```sql
SELECT p.Product_Name,
       m.Membership_Type
FROM Products p
CROSS JOIN Memberships m;
```

---

# MULTIPLE TABLE JOINS

## Example

```sql
SELECT c.Customer_Name,
       p.Product_Name,
       p.Price,
       m.Membership_Type
FROM Orders o
INNER JOIN Customers c
ON o.Customer_ID = c.Customer_ID
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
LEFT JOIN Memberships m
ON c.Customer_ID = m.Customer_ID;
```

---

# JOIN + GROUP BY

## Total Spending By Customer

```sql
SELECT c.Customer_Name,
       SUM(p.Price * o.Quantity) AS Total_Spending
FROM Orders o
INNER JOIN Customers c
ON o.Customer_ID = c.Customer_ID
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
GROUP BY c.Customer_Name;
```

---

# JOIN + HAVING

## Customers Spending More Than 50000

```sql
SELECT c.Customer_Name,
       SUM(p.Price * o.Quantity) AS Total_Spending
FROM Orders o
INNER JOIN Customers c
ON o.Customer_ID = c.Customer_ID
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
GROUP BY c.Customer_Name
HAVING SUM(p.Price * o.Quantity) > 50000;
```

---

# Real-Time Scenarios

## Find Customers Without Membership

```sql
SELECT c.Customer_Name
FROM Customers c
LEFT JOIN Memberships m
ON c.Customer_ID = m.Customer_ID
WHERE m.Customer_ID IS NULL;
```

---

## Find Membership Records Without Customers

```sql
SELECT *
FROM Memberships m
LEFT JOIN Customers c
ON m.Customer_ID = c.Customer_ID
WHERE c.Customer_ID IS NULL;
```

---

## Find Highest Revenue Product

```sql
SELECT p.Product_Name,
       SUM(p.Price * o.Quantity) Revenue
FROM Orders o
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
GROUP BY p.Product_Name
ORDER BY Revenue DESC;
```

---

# Section D – Short Answer Questions

1. What is a Primary Key?
2. What is a Foreign Key?
3. What is INNER JOIN?
4. What is LEFT JOIN?
5. What is RIGHT JOIN?
6. What is FULL OUTER JOIN?
7. What is SELF JOIN?
8. What is CROSS JOIN?
9. What is a Multiple Table Join?
10. Difference between INNER and LEFT JOIN?

---

# Section F – Write SQL Queries

1. Display customer names and orders.
2. Display customer names and membership type.
3. Display all customers including non-members.
4. Display memberships without customers.
5. Display employees and managers.
6. Display all product-membership combinations.
7. Display customer name and product purchased.
8. Display customer, product and membership information.
9. Find total spending by customer.
10. Find total spending by city.
11. Find total revenue by product.
12. Find products sold more than 3 times.
13. Find customers spending more than 50000.
14. Find Prime members.
15. Find non-members.
16. Find highest revenue product.
17. Find most ordered product.
18. Find Furniture purchases.
19. Find Electronics purchases.
20. Find city-wise order count.

---

# Section G – Debug SQL

### 1

```sql
SELECT *
FROM Customers
JOIN Orders;
```

### 2

```sql
SELECT *
FROM Customers c
LEFT Memberships m
ON c.Customer_ID = m.Customer_ID;
```

### 3

```sql
SELECT *
FROM Employees e
SELF JOIN Employees m
ON e.Manager_ID = m.Employee_ID;
```

### 4

```sql
SELECT Customer_Name,
       SUM(Price)
FROM Orders;
```

### 5

```sql
SELECT Product_Name,
       COUNT(*)
FROM Orders o
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
HAVING COUNT(*) > 3;
```

---

# Final Summary

✔ Primary Key

✔ Foreign Key

✔ INNER JOIN

✔ LEFT JOIN

✔ RIGHT JOIN

✔ FULL OUTER JOIN

✔ SELF JOIN

✔ CROSS JOIN

✔ Multiple Table Joins

✔ JOIN + GROUP BY

✔ JOIN + HAVING

✔ Real-Time Scenarios

✔ Interview-Oriented SQL Problems

---

# End of Day 5 & Day 6 Notes and Workbook

This combined module aligns with your syllabus:

Day 5: PK, FK, INNER, LEFT, RIGHT

Day 6: FULL OUTER, SELF, CROSS, Multiple Joins, Real-Time Scenarios


and is suitable for a single extended session (especially since you mentioned you have extra hours each day).
# SELF JOIN

## Definition

A table joined with itself.

### Example

```sql
SELECT e.Employee_Name,
       m.Employee_Name AS Manager
FROM Employees e
LEFT JOIN Employees m
ON e.Manager_ID = m.Employee_ID;
```

---

# CROSS JOIN

## Definition

Returns every possible combination.

### Formula

```text
Rows A × Rows B
```

### Example

```sql
SELECT p.Product_Name,
       m.Membership_Type
FROM Products p
CROSS JOIN Memberships m;
```

---

# MULTIPLE TABLE JOINS

## Example

```sql
SELECT c.Customer_Name,
       p.Product_Name,
       p.Price,
       m.Membership_Type
FROM Orders o
INNER JOIN Customers c
ON o.Customer_ID = c.Customer_ID
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
LEFT JOIN Memberships m
ON c.Customer_ID = m.Customer_ID;
```

---

# JOIN + GROUP BY

## Total Spending By Customer

```sql
SELECT c.Customer_Name,
       SUM(p.Price * o.Quantity) AS Total_Spending
FROM Orders o
INNER JOIN Customers c
ON o.Customer_ID = c.Customer_ID
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
GROUP BY c.Customer_Name;
```

---

# JOIN + HAVING

## Customers Spending More Than 50000

```sql
SELECT c.Customer_Name,
       SUM(p.Price * o.Quantity) AS Total_Spending
FROM Orders o
INNER JOIN Customers c
ON o.Customer_ID = c.Customer_ID
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
GROUP BY c.Customer_Name
HAVING SUM(p.Price * o.Quantity) > 50000;
```

---

# Real-Time Scenarios

## Find Customers Without Membership

```sql
SELECT c.Customer_Name
FROM Customers c
LEFT JOIN Memberships m
ON c.Customer_ID = m.Customer_ID
WHERE m.Customer_ID IS NULL;
```

---

## Find Membership Records Without Customers

```sql
SELECT *
FROM Memberships m
LEFT JOIN Customers c
ON m.Customer_ID = c.Customer_ID
WHERE c.Customer_ID IS NULL;
```

---

## Find Highest Revenue Product

```sql
SELECT p.Product_Name,
       SUM(p.Price * o.Quantity) Revenue
FROM Orders o
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
GROUP BY p.Product_Name
ORDER BY Revenue DESC;
```

---

# Section D – Short Answer Questions

1. What is a Primary Key?
2. What is a Foreign Key?
3. What is INNER JOIN?
4. What is LEFT JOIN?
5. What is RIGHT JOIN?
6. What is FULL OUTER JOIN?
7. What is SELF JOIN?
8. What is CROSS JOIN?
9. What is a Multiple Table Join?
10. Difference between INNER and LEFT JOIN?

---

# Section F – Write SQL Queries

1. Display customer names and orders.
2. Display customer names and membership type.
3. Display all customers including non-members.
4. Display memberships without customers.
5. Display employees and managers.
6. Display all product-membership combinations.
7. Display customer name and product purchased.
8. Display customer, product and membership information.
9. Find total spending by customer.
10. Find total spending by city.
11. Find total revenue by product.
12. Find products sold more than 3 times.
13. Find customers spending more than 50000.
14. Find Prime members.
15. Find non-members.
16. Find highest revenue product.
17. Find most ordered product.
18. Find Furniture purchases.
19. Find Electronics purchases.
20. Find city-wise order count.

---

# Section G – Debug SQL

### 1

```sql
SELECT *
FROM Customers
JOIN Orders;
```

### 2

```sql
SELECT *
FROM Customers c
LEFT Memberships m
ON c.Customer_ID = m.Customer_ID;
```

### 3

```sql
SELECT *
FROM Employees e
SELF JOIN Employees m
ON e.Manager_ID = m.Employee_ID;
```

### 4

```sql
SELECT Customer_Name,
       SUM(Price)
FROM Orders;
```

### 5

```sql
SELECT Product_Name,
       COUNT(*)
FROM Orders o
INNER JOIN Products p
ON o.Product_ID = p.Product_ID
HAVING COUNT(*) > 3;
```

---

# Final Summary

✔ Primary Key

✔ Foreign Key

✔ INNER JOIN

✔ LEFT JOIN

✔ RIGHT JOIN

✔ FULL OUTER JOIN

✔ SELF JOIN

✔ CROSS JOIN

✔ Multiple Table Joins

✔ JOIN + GROUP BY

✔ JOIN + HAVING

✔ Real-Time Scenarios

✔ Interview-Oriented SQL Problems

---

# End of Day 5 & Day 6 Notes and Workbook

This combined module aligns with your syllabus:

Day 5: PK, FK, INNER, LEFT, RIGHT

Day 6: FULL OUTER, SELF, CROSS, Multiple Joins, Real-Time Scenarios


and is suitable for a single extended session (especially since you mentioned you have extra hours each day).
