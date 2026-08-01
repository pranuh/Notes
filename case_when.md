

# Story Before Learning CASE WHEN

Imagine Amazon wants to classify orders as:

- High Value Orders
- Medium Value Orders
- Low Value Orders

Can we create a new column directly in SQL?

Yes.

We use **CASE WHEN**.

CASE WHEN works like:

```text
IF
ELSE IF
ELSE
```

in programming languages.

---

# Simple Definition

CASE WHEN allows us to apply conditions and return different values based on those conditions.

---

# Syntax

```sql
SELECT column_name,
       CASE
           WHEN condition1 THEN result1
           WHEN condition2 THEN result2
           ELSE result3
       END AS alias_name
FROM table_name;
```

---

# Sample Dataset

## Table: Superstore_Orders

| Order ID | Customer Name | Category | Sales | Profit |
|-----------|--------------|-----------|--------|--------|
| CA-101 | Rahul | Furniture | 120 | 20 |
| CA-102 | Priya | Technology | 650 | 150 |
| CA-103 | Arjun | Office Supplies | 50 | -10 |
| CA-104 | Sneha | Furniture | 900 | 200 |
| CA-105 | Kiran | Technology | 300 | 40 |

---

# Example 1: Basic CASE WHEN

Classify Orders

```sql
SELECT Order_ID,
       Sales,
       CASE
           WHEN Sales >= 500 THEN 'High Value'
           ELSE 'Regular'
       END AS Order_Type
FROM Superstore_Orders;
```

---

# Output

| Order_ID | Sales | Order_Type |
|-----------|--------|------------|
| CA-101 | 120 | Regular |
| CA-102 | 650 | High Value |
| CA-103 | 50 | Regular |
| CA-104 | 900 | High Value |

---

# Example 2: Multiple Conditions

```sql
SELECT Order_ID,
       Sales,
       CASE
           WHEN Sales >= 500 THEN 'High'
           WHEN Sales >= 200 THEN 'Medium'
           ELSE 'Low'
       END AS Sales_Category
FROM Superstore_Orders;
```

---

# Output

| Sales | Category |
|--------|-----------|
| 900 | High |
| 300 | Medium |
| 50 | Low |

---

# Example 3: Profit Status

```sql
SELECT Order_ID,
       Profit,
       CASE
           WHEN Profit > 0 THEN 'Profit'
           WHEN Profit < 0 THEN 'Loss'
           ELSE 'Break Even'
       END AS Profit_Status
FROM Superstore_Orders;
```

---

# Real Business Example

Amazon Management asks:

Which orders are profitable?

```sql
SELECT Order_ID,
       Profit,
       CASE
           WHEN Profit > 0 THEN 'Profitable'
           ELSE 'Loss Making'
       END AS Business_Status
FROM Superstore_Orders;
```

---

# CASE WHEN with Aggregate Functions

## Example 4

Find number of profitable and loss-making orders.

```sql
SELECT
       CASE
           WHEN Profit > 0 THEN 'Profit'
           ELSE 'Loss'
       END AS Status,
       COUNT(*) AS Total_Orders
FROM Superstore_Orders
GROUP BY
       CASE
           WHEN Profit > 0 THEN 'Profit'
           ELSE 'Loss'
       END;
```

---

# Output

| Status | Total_Orders |
|----------|------------|
| Profit | 4500 |
| Loss | 1200 |

---

# CASE WHEN with SUM()

Calculate sales contribution by category.

```sql
SELECT
       SUM(
           CASE
               WHEN Category='Furniture'
               THEN Sales
               ELSE 0
           END
       ) AS Furniture_Sales
FROM Superstore_Orders;
```

---

# Example 5

Technology Sales

```sql
SELECT
       SUM(
           CASE
               WHEN Category='Technology'
               THEN Sales
               ELSE 0
           END
       ) AS Technology_Sales
FROM Superstore_Orders;
```

---

# CASE WHEN with COUNT()

Count profitable orders.

```sql
SELECT
       COUNT(
           CASE
               WHEN Profit > 0
               THEN 1
           END
       ) AS Profitable_Orders
FROM Superstore_Orders;
```

---

# Example 6: Customer Segmentation

```sql
SELECT Customer_Name,
       Sales,
       CASE
           WHEN Sales >= 1000 THEN 'Premium'
           WHEN Sales >= 500 THEN 'Gold'
           WHEN Sales >= 100 THEN 'Silver'
           ELSE 'Bronze'
       END AS Customer_Tier
FROM Superstore_Orders;
```

---

# Example 7: Region Classification

```sql
SELECT Region,
       CASE
           WHEN Region IN ('East','West')
           THEN 'Developed'
           ELSE 'Emerging'
       END AS Market_Type
FROM Superstore_Orders;
```

---

# CASE WHEN vs WHERE

## WHERE

Filters rows.

```sql
SELECT *
FROM Superstore_Orders
WHERE Sales > 500;
```

---

## CASE WHEN

Creates categories.

```sql
SELECT Sales,
       CASE
           WHEN Sales > 500
           THEN 'High'
           ELSE 'Low'
       END
FROM Superstore_Orders;
```

---

# Common Mistakes

## Missing END

Wrong

```sql
SELECT CASE
       WHEN Sales > 500
       THEN 'High'
FROM Superstore_Orders;
```

Correct

```sql
SELECT CASE
       WHEN Sales > 500
       THEN 'High'
       END
FROM Superstore_Orders;
```

---

## Missing ELSE

Allowed but NULL may appear.

```sql
SELECT CASE
       WHEN Sales > 500
       THEN 'High'
       END
FROM Superstore_Orders;
```

---

# SQL Execution Reminder

```text
FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
```

CASE WHEN is usually written inside SELECT.

---

# Day Summary

You should now be able to:

- Use CASE WHEN
- Create custom labels
- Create categories
- Generate conditional reports
- Use CASE WHEN with COUNT()
- Use CASE WHEN with SUM()
- Use CASE WHEN with GROUP BY
- Build business-friendly dashboards

---

# Section D – Short Answer Questions

1. What is CASE WHEN?

2. Why is CASE WHEN used?

3. What is the purpose of ELSE?

4. Can CASE WHEN have multiple conditions?

5. What happens if ELSE is not used?

6. Difference between CASE WHEN and WHERE?

7. Can CASE WHEN be used with SUM()?

8. Can CASE WHEN be used with COUNT()?

9. Can CASE WHEN be used with GROUP BY?

10. Which programming concept is similar to CASE WHEN?

---

# Section F – Write SQL Queries

1. Display High Value and Regular Orders using Sales.

2. Classify orders as High, Medium and Low Sales.

3. Display Profit and Loss orders.

4. Create Customer Tiers (Premium, Gold, Silver, Bronze).

5. Display Furniture and Non-Furniture orders.

6. Display Technology and Non-Technology orders.

7. Count profitable orders using CASE WHEN.

8. Count loss-making orders using CASE WHEN.

9. Find total Furniture sales using CASE WHEN.

10. Find total Technology sales using CASE WHEN.

11. Display East/West as Developed Markets and others as Emerging Markets.

12. Create a column showing "Bulk Order" when Quantity > 5.

13. Display "Discounted Order" when Discount > 0.

14. Classify profits as High Profit, Medium Profit and Low Profit.

15. Display "Top Customer" when Sales > 1000.

16. Count orders in each Sales Category.

17. Calculate total sales for Premium customers.

18. Calculate total sales for Gold customers.

19. Display profitable Furniture orders.

20. Display loss-making Technology orders.

---

# Section G – Find the Error

## 1

```sql
SELECT CASE
       WHEN Sales > 500
       THEN 'High'
FROM Superstore_Orders;
```

---

## 2

```sql
SELECT Sales,
       CASE Sales > 500
       THEN 'High'
       ELSE 'Low'
       END
FROM Superstore_Orders;
```

---

## 3

```sql
SELECT CASE
       WHEN Profit > 0
       'Profit'
       ELSE 'Loss'
       END
FROM Superstore_Orders;
```

---

## 4

```sql
SELECT SUM(
       CASE
       WHEN Category='Furniture'
       THEN Sales
       )
FROM Superstore_Orders;
```

---

## 5

```sql
SELECT CASE
       WHEN Sales > 500
       THEN High
       ELSE Low
       END
FROM Superstore_Orders;
```

---

