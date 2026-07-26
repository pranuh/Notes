# Day 2: SQL Data Retrieval and Filtering

**Syllabus Mapping:** Day 2 – SELECT, WHERE, Arithmetic Operators, Comparison Operators, Logical Operators, NULL Handling

# Employees Table - SQL Script

## Create Table

```sql
CREATE TABLE Employees (
    Emp_ID INT PRIMARY KEY,
    Emp_Name VARCHAR(50),
    Department VARCHAR(20),
    Salary INT,
    Bonus INT,
    Experience INT,
    City VARCHAR(30)
);
```

---

## Insert Records

```sql
INSERT INTO Employees
(Emp_ID, Emp_Name, Department, Salary, Bonus, Experience, City)
VALUES
(101, 'Arun', 'IT', 50000, 5000, 2, 'Bangalore'),
(102, 'Bhavna', 'HR', 45000, NULL, 3, 'Hyderabad'),
(103, 'Charan', 'Sales', 55000, 7000, 5, 'Chennai'),
(104, 'Divya', 'IT', 60000, 8000, 6, 'Bangalore'),
(105, 'Eshwar', 'Finance', 65000, NULL, 8, 'Pune'),
(106, 'Farah', 'Sales', 48000, 3000, 2, 'Chennai'),
(107, 'Ganesh', 'HR', 42000, 2000, 1, 'Hyderabad'),
(108, 'Harika', 'IT', 70000, 10000, 10, 'Bangalore'),
(109, 'Imran', 'Finance', 58000, 4000, 4, 'Mumbai'),
(110, 'Jyothi', 'Sales', 52000, NULL, 3, 'Chennai'),
(111, 'Kiran', 'IT', 62000, 6000, 7, 'Bangalore'),
(112, 'Lakshmi', 'HR', 47000, 2500, 2, 'Hyderabad'),
(113, 'Manoj', 'Finance', 75000, 12000, 12, 'Pune'),
(114, 'Nisha', 'Sales', 53000, 3500, 4, 'Chennai'),
(115, 'Omkar', 'IT', 68000, NULL, 9, 'Bangalore'),
(116, 'Priya', 'HR', 49000, 2000, 3, 'Hyderabad'),
(117, 'Qasim', 'Finance', 61000, 5000, 5, 'Mumbai'),
(118, 'Rani', 'Sales', 56000, 4500, 6, 'Chennai'),
(119, 'Suresh', 'IT', 72000, 9000, 11, 'Bangalore'),
(120, 'Teja', 'Finance', 59000, NULL, 4, 'Pune');
```

---

## Verify Data

```sql
SELECT * FROM Employees;
```

---

## Check Total Records

```sql
SELECT COUNT(*) AS Total_Employees
FROM Employees;
```

Expected Output:

```text
Total_Employees
---------------
20
```
---

# Sample Database

## Table: Employees

| Emp_ID | Emp_Name | Department | Salary | Bonus | Experience | City |
|---------|----------|------------|---------|---------|------------|---------|
| 101 | Arun | IT | 50000 | 5000 | 2 | Bangalore |
| 102 | Bhavna | HR | 45000 | NULL | 3 | Hyderabad |
| 103 | Charan | Sales | 55000 | 7000 | 5 | Chennai |
| 104 | Divya | IT | 60000 | 8000 | 6 | Bangalore |
| 105 | Eshwar | Finance | 65000 | NULL | 8 | Pune |
| 106 | Farah | Sales | 48000 | 3000 | 2 | Chennai |
| 107 | Ganesh | HR | 42000 | 2000 | 1 | Hyderabad |
| 108 | Harika | IT | 70000 | 10000 | 10 | Bangalore |
| 109 | Imran | Finance | 58000 | 4000 | 4 | Mumbai |
| 110 | Jyothi | Sales | 52000 | NULL | 3 | Chennai |
| 111 | Kiran | IT | 62000 | 6000 | 7 | Bangalore |
| 112 | Lakshmi | HR | 47000 | 2500 | 2 | Hyderabad |
| 113 | Manoj | Finance | 75000 | 12000 | 12 | Pune |
| 114 | Nisha | Sales | 53000 | 3500 | 4 | Chennai |
| 115 | Omkar | IT | 68000 | NULL | 9 | Bangalore |
| 116 | Priya | HR | 49000 | 2000 | 3 | Hyderabad |
| 117 | Qasim | Finance | 61000 | 5000 | 5 | Mumbai |
| 118 | Rani | Sales | 56000 | 4500 | 6 | Chennai |
| 119 | Suresh | IT | 72000 | 9000 | 11 | Bangalore |
| 120 | Teja | Finance | 59000 | NULL | 4 | Pune |

---

# Part 1 – Student Notes

# 1. SELECT Statement

## Simple Definition

The SELECT statement is used to retrieve data from a table.

## Why it is Used

- To view records from a table
- To retrieve specific columns
- To analyze data

## Syntax

```sql
SELECT column_name
FROM table_name;
```

```sql
SELECT *
FROM table_name;
```

## Examples

```sql
SELECT * FROM Employees;
```

```sql
SELECT Emp_Name FROM Employees;
```

```sql
SELECT Emp_Name, Salary
FROM Employees;
```

```sql
SELECT Department
FROM Employees;
```

```sql
SELECT City, Department
FROM Employees;
```

## Important Points

- SELECT retrieves data.
- * means all columns.
- Multiple columns are separated by commas.
- SQL keywords are not case-sensitive.

## Common Mistakes

```sql
SELECT Emp_Name;
```

```sql
SELECT EmpNme FROM Employees;
```

## Short Summary

SELECT is used to fetch data from one or more columns of a table.

---

# 2. WHERE Clause

## Simple Definition

WHERE filters rows based on a condition.

## Why it is Used

- Retrieve specific records
- Reduce unwanted data
- Apply conditions

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

## Examples

```sql
SELECT *
FROM Employees
WHERE Department='IT';
```

```sql
SELECT *
FROM Employees
WHERE Salary > 60000;
```

```sql
SELECT *
FROM Employees
WHERE City='Hyderabad';
```

```sql
SELECT Emp_Name, Salary
FROM Employees
WHERE Experience >= 5;
```

```sql
SELECT *
FROM Employees
WHERE Department='Finance';
```

## Important Points

- WHERE filters rows.
- Conditions must evaluate to TRUE.
- Strings should be enclosed in quotes.

## Common Mistakes

```sql
WHERE Department = IT
```

## Short Summary

WHERE helps retrieve only the required rows.

---

# 3. Arithmetic Operators

## Simple Definition

Arithmetic operators perform mathematical calculations.

## Why it is Used

- Calculate totals
- Calculate increments
- Generate reports

## Operators

| Operator | Meaning |
|----------|----------|
| + | Addition |
| - | Subtraction |
| * | Multiplication |
| / | Division |

## Syntax

```sql
SELECT column1 + column2
FROM table_name;
```

## Examples

```sql
SELECT Salary + Bonus
FROM Employees;
```

```sql
SELECT Salary - 2000
FROM Employees;
```

```sql
SELECT Salary * 12
FROM Employees;
```

```sql
SELECT Salary / 2
FROM Employees;
```

```sql
SELECT Emp_Name,
       Salary + 5000
FROM Employees;
```

## Important Points

- Arithmetic operations can be performed on numeric columns.
- NULL in calculations often returns NULL.

## Common Mistakes

- Using arithmetic operators on text data.
- Ignoring NULL values.

## Short Summary

Arithmetic operators help perform calculations in SQL queries.

---

# 4. Comparison Operators

## Simple Definition

Comparison operators compare values.

## Why it is Used

- Filter data
- Compare numeric values
- Compare text values

## Operators

| Operator | Meaning |
|----------|----------|
| = | Equal |
| > | Greater Than |
| < | Less Than |
| >= | Greater Than or Equal |
| <= | Less Than or Equal |
| <> | Not Equal |

## Examples

```sql
SELECT *
FROM Employees
WHERE Salary = 50000;
```

```sql
SELECT *
FROM Employees
WHERE Salary > 60000;
```

```sql
SELECT *
FROM Employees
WHERE Experience < 5;
```

```sql
SELECT *
FROM Employees
WHERE Department <> 'IT';
```

```sql
SELECT *
FROM Employees
WHERE Salary >= 65000;
```

## Important Points

- Used mainly with WHERE.
- Can compare numbers and strings.

## Common Mistakes

```sql
WHERE Salary == 50000
```

## Short Summary

Comparison operators are used to compare values and filter records.


# 5. Logical Operators

## Simple Definition

Logical operators combine multiple conditions.

## Why it is Used

- Apply multiple filters
- Build complex conditions

## Operators

| Operator | Meaning |
|----------|----------|
| AND | All conditions true |
| OR | Any condition true |
| NOT | Opposite condition |

## Examples

```sql
SELECT *
FROM Employees
WHERE Department='IT'
AND Salary > 60000;
```

```sql
SELECT *
FROM Employees
WHERE Department='HR'
OR Department='Finance';
```

```sql
SELECT *
FROM Employees
WHERE NOT Department='Sales';
```

```sql
SELECT *
FROM Employees
WHERE City='Bangalore'
AND Experience > 5;
```

```sql
SELECT *
FROM Employees
WHERE Salary > 50000
OR Experience > 8;
```

## Important Points

- AND narrows results.
- OR increases results.
- NOT reverses conditions.

## Common Mistakes

- Incorrect condition grouping.
- Forgetting logical operators between conditions.

## Short Summary

Logical operators help combine multiple conditions.

## My Notes

____________________________________

____________________________________

____________________________________

---

# 6. NULL Handling

## Simple Definition

NULL represents missing or unknown data.

## Why it is Used

- Handle incomplete data
- Identify missing values

## Syntax

```sql
WHERE column IS NULL
```

```sql
WHERE column IS NOT NULL
```

## Examples

```sql
SELECT *
FROM Employees
WHERE Bonus IS NULL;
```

```sql
SELECT *
FROM Employees
WHERE Bonus IS NOT NULL;
```

```sql
SELECT Emp_Name
FROM Employees
WHERE Bonus IS NULL;
```

```sql
SELECT Emp_Name, Bonus
FROM Employees
WHERE Bonus IS NULL;
```

## Important Points

- NULL is not zero.
- NULL is not an empty string.
- Use IS NULL or IS NOT NULL.

## Common Mistakes

```sql
WHERE Bonus = NULL
```

Correct:

```sql
WHERE Bonus IS NULL
```

## Short Summary

NULL handling helps identify missing values correctly.

---

# Part 2 – Practice Workbook

## Short Answer Questions

1. What is the purpose of SELECT?
2. What is the use of WHERE clause?
3. What is NULL?
4. Name any four comparison operators.
5. What is the difference between AND and OR?
6. Why do we use arithmetic operators?
7. What does SELECT * do?
8. What is IS NULL used for?

---

## Write SQL Queries

1. Display all employee details.
2. Display Employee Name and Salary.
3. Display employees working in IT department.
4. Display employees whose salary is greater than 60000.
5. Display employees from Hyderabad.
6. Display employees with experience greater than 5 years.
7. Display employees whose salary is less than 50000.
8. Display employees from Finance department.
9. Display employees whose bonus is NULL.
10. Display employees whose bonus is not NULL.
11. Display employees from Bangalore and salary greater than 60000.
12. Display employees from HR or Finance department.
13. Display employees not belonging to Sales department.
14. Display employee name and annual salary.
15. Display employee name and salary after adding 5000.

---

## Find the Error (Debug SQL)

### 1

```sql
SELECT FROM Employees;
```

### 2

```sql
SELECT Emp_Name Salary
Employees;
```

### 3

```sql
SELECT *
FROM Employees
WHERE Department = IT;
```

### 4

```sql
SELECT *
FROM Employees
WHERE Salary >> 50000;
```

### 5

```sql
SELECT *
FROM Employees
WHERE Bonus = NULL;
```

### 6

```sql
SELECT *
FROM Employees
WHERE Department='IT'
Salary > 60000;
```

### 7

```sql
SELECT *
Employees
WHERE Salary > 50000;
```

### 8

```sql
SELECT *
FROM Employees
WHERE Experience => 5;
```

---

## Mini Assessment

1. Write a query to display employees from Bangalore whose salary is greater than 65000.

2. Write a query to display employees from Hyderabad or Pune.

3. Write a query to display employees with salary between 50000 and 65000 using logical operators.

4. Write a query to display employees whose bonus is missing.

5. Write a query to display employees whose department is not HR.

6. Write a query to display employee name and annual salary.

7. Write a query to display employees with experience greater than 5 years and salary greater than 60000.

8. Predict the output:

```sql
SELECT Emp_Name
FROM Employees
WHERE Bonus IS NOT NULL
AND Salary > 55000;
```

9. Predict the output:

```sql
SELECT Emp_Name
FROM Employees
WHERE Department='IT'
OR Department='Finance';
```

10. Write a query to display employees whose city is Chennai and bonus is not NULL.

---
