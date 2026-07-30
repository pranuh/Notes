# Day 4: Functions and Grouping

** Day 4 – Single Row Functions, Aggregate Functions, COUNT, SUM, AVG, MIN, MAX, GROUP BY, HAVING

---

# Sample Database

## Table: Superstore_Orders

| Row ID | Order ID | Order Date | Ship Date | Ship Mode | Customer ID | Customer Name | Segment | Country | City | State | Postal Code | Region | Product ID | Category | Sub-Category | Product Name | Sales | Quantity | Discount | Profit |
|---------|----------|------------|------------|------------|-------------|---------------|----------|----------|------|--------|-------------|--------|------------|----------|--------------|--------------|--------|----------|----------|--------|
| 1 | CA-2016-152156 | 11/8/2016 | 11/11/2016 | Second Class | CG-12520 | Claire Gute | Consumer | United States | Henderson | Kentucky | 42420 | South | FUR-BO-10001798 | Furniture | Bookcases | Bush Somerset Collection Bookcase | 261.96 | 2 | 0 | 41.9136 |
| 2 | CA-2016-152156 | 11/8/2016 | 11/11/2016 | Second Class | CG-12520 | Claire Gute | Consumer | United States | Henderson | Kentucky | 42420 | South | FUR-CH-10000454 | Furniture | Chairs | Hon Deluxe Fabric Upholstered Chair | 731.94 | 3 | 0 | 219.582 |
| 3 | CA-2016-138688 | 6/12/2016 | 6/16/2016 | Second Class | DV-13045 | Darrin Van Huff | Corporate | United States | Los Angeles | California | 90036 | West | OFF-LA-10000240 | Office Supplies | Labels | Self-Adhesive Address Labels | 14.62 | 2 | 0 | 6.8714 |

*(Use the complete Superstore dataset with ~10,000 rows for classroom practice.)*

---

# Part 1 – Student Notes

# Day 3 Quick Recap

Previously we learned:

- DISTINCT
- ALIAS
- IN
- BETWEEN
- LIKE
- ORDER BY

Example:

```sql
SELECT *
FROM Superstore_Orders
WHERE Region = 'West'
ORDER BY Sales DESC;
```

---

# Introduction to Functions

Functions perform calculations on data and return results.

Functions help us:

- Format text
- Manipulate values
- Generate reports
- Analyze sales data
- Create business summaries

---

# Types of Functions

| Function Type | Description |
|--------------|-------------|
| Single Row Functions | Operate on one row at a time |
| Aggregate Functions | Operate on multiple rows |

---

# Single Row Functions

## Simple Definition

A Single Row Function processes one record at a time and returns one result for each row.

---

# Character Functions

Used to manipulate text values.

---

## UPPER()

Converts text into uppercase.

```sql
SELECT UPPER(Customer_Name)
FROM Superstore_Orders;
```

---

## LOWER()

Converts text into lowercase.

```sql
SELECT LOWER(Customer_Name)
FROM Superstore_Orders;
```

---

## LENGTH()

Returns number of characters.

```sql
SELECT Customer_Name,
       LENGTH(Customer_Name)
FROM Superstore_Orders;
```

---

## CONCAT()

Combines multiple values.

```sql
SELECT CONCAT(Customer_Name,' - ',City)
FROM Superstore_Orders;
```

Output:

```text
Claire Gute - Henderson
Darrin Van Huff - Los Angeles
```

---

## SUBSTRING()

Returns part of a string.

```sql
SELECT SUBSTRING(Customer_Name,1,4)
FROM Superstore_Orders;
```

---

## REPLACE()

Replaces text with another value.

```sql
SELECT REPLACE(Country,'United States','USA')
FROM Superstore_Orders;
```

---

## TRIM()

Removes extra spaces.

```sql
SELECT TRIM(Customer_Name)
FROM Superstore_Orders;
```

---

# Numeric Functions

Used for calculations.

---

## ROUND()

Rounds numbers.

```sql
SELECT ROUND(Sales)
FROM Superstore_Orders;
```

---

```sql
SELECT ROUND(Profit,2)
FROM Superstore_Orders;
```

---

## CEIL()

Rounds upward.

```sql
SELECT CEIL(Sales)
FROM Superstore_Orders;
```

---

## FLOOR()

Rounds downward.

```sql
SELECT FLOOR(Sales)
FROM Superstore_Orders;
```

---

## ABS()

Returns absolute value.

```sql
SELECT ABS(Profit)
FROM Superstore_Orders;
```

---

## MOD()

Returns remainder.

```sql
SELECT MOD(Quantity,2)
FROM Superstore_Orders;
```

---

# Aggregate Functions

## Simple Definition

Aggregate Functions operate on multiple rows and return a single summarized result.

---

# Why Aggregate Functions?

Business users frequently ask:

- Total Sales?
- Total Profit?
- Average Sales?
- Highest Sale?
- Lowest Sale?
- Sales by Region?
- Sales by Category?

Aggregate Functions answer these questions.

---

# Aggregate Functions Overview

| Function | Purpose |
|-----------|----------|
| COUNT() | Counts records |
| SUM() | Calculates total |
| AVG() | Calculates average |
| MIN() | Finds smallest value |
| MAX() | Finds largest value |

---

# COUNT()

## Count Total Records

```sql
SELECT COUNT(*)
FROM Superstore_Orders;
```

---

## Count Unique Customers

```sql
SELECT COUNT(DISTINCT Customer_ID)
FROM Superstore_Orders;
```

---

## Count Unique Cities

```sql
SELECT COUNT(DISTINCT City)
FROM Superstore_Orders;
```

---

# SUM()

## Total Sales

```sql
SELECT SUM(Sales)
FROM Superstore_Orders;
```

---

## Total Profit

```sql
SELECT SUM(Profit)
FROM Superstore_Orders;
```

---

# AVG()

## Average Sales

```sql
SELECT AVG(Sales)
FROM Superstore_Orders;
```

---

## Average Profit

```sql
SELECT AVG(Profit)
FROM Superstore_Orders;
```

---

# MIN()

## Lowest Sale

```sql
SELECT MIN(Sales)
FROM Superstore_Orders;
```

---

## Lowest Profit

```sql
SELECT MIN(Profit)
FROM Superstore_Orders;
```

---

# MAX()

## Highest Sale

```sql
SELECT MAX(Sales)
FROM Superstore_Orders;
```

---

## Highest Profit

```sql
SELECT MAX(Profit)
FROM Superstore_Orders;
```

---

# GROUP BY

## Simple Definition

GROUP BY creates groups and performs aggregate calculations on each group.

---

## Count Orders by Region

```sql
SELECT Region,
       COUNT(*) AS Total_Orders
FROM Superstore_Orders
GROUP BY Region;
```

---

## Sales by Category

```sql
SELECT Category,
       SUM(Sales) AS Total_Sales
FROM Superstore_Orders
GROUP BY Category;
```

---

## Profit by State

```sql
SELECT State,
       SUM(Profit) AS Total_Profit
FROM Superstore_Orders
GROUP BY State;
```

---

## Quantity Sold by Sub-Category

```sql
SELECT Sub_Category,
       SUM(Quantity)
FROM Superstore_Orders
GROUP BY Sub_Category;
```

---

# Multiple Column GROUP BY

```sql
SELECT Region,
       Category,
       SUM(Sales) AS Revenue
FROM Superstore_Orders
GROUP BY Region, Category;
```

---

# Important GROUP BY Rule

Every column in SELECT must be:

- Inside an Aggregate Function

OR

- Included in GROUP BY

Correct:

```sql
SELECT Region,
       COUNT(*)
FROM Superstore_Orders
GROUP BY Region;
```

Incorrect:

```sql
SELECT Region,
       Customer_Name,
       COUNT(*)
FROM Superstore_Orders
GROUP BY Region;
```

---

# HAVING Clause

## Simple Definition

HAVING filters grouped results.

---

# WHERE vs HAVING

| WHERE | HAVING |
|---------|---------|
| Filters rows | Filters groups |
| Before GROUP BY | After GROUP BY |
| Cannot use aggregate functions | Can use aggregate functions |

---

## Example 1

Regions having more than 100 orders.

```sql
SELECT Region,
       COUNT(*) AS Total_Orders
FROM Superstore_Orders
GROUP BY Region
HAVING COUNT(*) > 100;
```

---

## Example 2

Categories having sales greater than 50000.

```sql
SELECT Category,
       SUM(Sales) AS Total_Sales
FROM Superstore_Orders
GROUP BY Category
HAVING SUM(Sales) > 50000;
```

---

## Example 3

States having average profit greater than 50.

```sql
SELECT State,
       AVG(Profit)
FROM Superstore_Orders
GROUP BY State
HAVING AVG(Profit) > 50;
```

---

# WHERE + GROUP BY + HAVING

```sql
SELECT Category,
       SUM(Sales) AS Total_Sales
FROM Superstore_Orders
WHERE Discount = 0
GROUP BY Category
HAVING SUM(Sales) > 50000;
```

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

# Day 4 Summary

You should now be able to:

- Use Character Functions
- Use Numeric Functions
- Use COUNT()
- Use COUNT(DISTINCT)
- Use SUM()
- Use AVG()
- Use MIN()
- Use MAX()
- Create groups using GROUP BY
- Create multi-column groups
- Filter groups using HAVING
- Differentiate WHERE and HAVING
- Generate business reports and summaries

---

# Part 2 – Practice Workbook

## Section D – Short Answer Questions

1. What is a Single Row Function?

2. What is an Aggregate Function?

3. What is the purpose of UPPER()?

4. What is the purpose of CONCAT()?

5. What is the difference between COUNT(*) and COUNT(DISTINCT)?

6. What does SUM() calculate?

7. Why do we use GROUP BY?

8. What is the purpose of HAVING?

9. Difference between WHERE and HAVING?

10. Name three Numeric Functions.

---

## Section F – Write SQL Queries

### Single Row Functions

1. Display all customer names in uppercase.

2. Display all customer names in lowercase.

3. Display the length of each customer name.

4. Display customer name and city together.

5. Display first four characters of each customer name.

6. Replace "United States" with "USA".

7. Display sales rounded to nearest integer.

8. Display profit rounded to two decimal places.

9. Display quantity divided by two and rounded to one decimal place.

10. Display absolute value of profit.

---

### Aggregate Functions

11. Find total number of orders.

12. Find total sales.

13. Find total profit.

14. Find average sales.

15. Find average profit.

16. Find maximum sales.

17. Find minimum sales.

18. Find maximum profit.

19. Find minimum profit.

20. Count unique customers.

21. Count unique cities.

22. Count unique states.

23. Count unique categories.

---

### GROUP BY Queries

24. Count orders by Region.

25. Count orders by Category.

26. Count orders by Segment.

27. Find total sales by Region.

28. Find total sales by Category.

29. Find total sales by Segment.

30. Find average sales by Region.

31. Find average profit by Category.

32. Find maximum sales by Region.

33. Find minimum profit by Category.

34. Find total quantity sold by Category.

35. Find total quantity sold by Sub-Category.

36. Find total sales by State.

37. Find total profit by State.

38. Find total sales by Region and Category.

39. Find total sales by Category and Sub-Category.

40. Find average profit by Region and Segment.

---

### HAVING Queries

41. Display regions having more than 50 orders.

42. Display states having total sales greater than 10000.

43. Display categories having average sales greater than 500.

44. Display segments having total profit greater than 1000.

45. Display sub-categories having more than 20 orders.

46. Display regions having average profit greater than 50.

47. Display states having total quantity greater than 100.

48. Display category and sub-category combinations having sales greater than 5000.

49. Display customers whose total purchase value exceeds 2000.

50. Display cities having more than 10 unique customers.

---

## Section G – Find the Error (Debug SQL)

### 1

```sql
SELECT SUM
FROM Superstore_Orders;
```

### 2

```sql
SELECT Region,
       SUM(Sales)
FROM Superstore_Orders;
```

### 3

```sql
SELECT Category,
       AVG(Sales)
FROM Superstore_Orders
HAVING AVG(Sales) > 500;
```

### 4

```sql
SELECT COUNT(DISTINCT)
FROM Superstore_Orders;
```

### 5

```sql
SELECT Region,
       Sales
FROM Superstore_Orders
GROUP BY Region;
```

### 6

```sql
SELECT MAX(Sales, Profit)
FROM Superstore_Orders;
```

### 7

```sql
SELECT Category,
       SUM(Sales)
FROM Superstore_Orders
GROUP Category;
```

### 8

```sql
SELECT Region,
       COUNT(*)
FROM Superstore_Orders
GROUP BY Region
WHERE COUNT(*) > 10;
```

---

# End of Day 4 Notes and Workbook
