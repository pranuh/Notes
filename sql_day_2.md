Day 2: SQL Data Retrieval and Filtering

Syllabus Mapping: Day 2 – SELECT, WHERE, Arithmetic Operators, Comparison Operators, Logical Operators, NULL Handling

Book Mapping (Learning SQL by Alan Beaulieu):

Chapter 3: Query Basics (SELECT, WHERE)

Chapter 4: Filtering Data

Chapter 5: Working with Expressions and Conditions



---

Sample Database

Use the following table for all examples and practice questions.

Table: Employees

Emp_ID	Emp_Name	Department	Salary	Bonus	Experience	City

101	Arun	IT	50000	5000	2	Bangalore
102	Bhavna	HR	45000	NULL	3	Hyderabad
103	Charan	Sales	55000	7000	5	Chennai
104	Divya	IT	60000	8000	6	Bangalore
105	Eshwar	Finance	65000	NULL	8	Pune
106	Farah	Sales	48000	3000	2	Chennai
107	Ganesh	HR	42000	2000	1	Hyderabad
108	Harika	IT	70000	10000	10	Bangalore
109	Imran	Finance	58000	4000	4	Mumbai
110	Jyothi	Sales	52000	NULL	3	Chennai
111	Kiran	IT	62000	6000	7	Bangalore
112	Lakshmi	HR	47000	2500	2	Hyderabad
113	Manoj	Finance	75000	12000	12	Pune
114	Nisha	Sales	53000	3500	4	Chennai
115	Omkar	IT	68000	NULL	9	Bangalore
116	Priya	HR	49000	2000	3	Hyderabad
117	Qasim	Finance	61000	5000	5	Mumbai
118	Rani	Sales	56000	4500	6	Chennai
119	Suresh	IT	72000	9000	11	Bangalore
120	Teja	Finance	59000	NULL	4	Pune



---

Part 1 – Student Notes (3 Hours)

1. SELECT Statement

Simple Definition

The SELECT statement is used to retrieve data from a table.

Why it is Used

To view records from a table

To retrieve specific columns

To analyze data


Syntax

SELECT column_name
FROM table_name;

SELECT *
FROM table_name;

Examples

Example 1

SELECT * FROM Employees;

Example 2

SELECT Emp_Name FROM Employees;

Example 3

SELECT Emp_Name, Salary
FROM Employees;

Example 4

SELECT Department
FROM Employees;

Example 5

SELECT City, Department
FROM Employees;

Important Points

SELECT retrieves data.

means all columns.


Multiple columns are separated by commas.

SQL keywords are not case-sensitive.


Common Mistakes

❌ Missing FROM clause

SELECT Emp_Name;

❌ Misspelled column name

SELECT EmpNme FROM Employees;

Short Summary

SELECT is used to fetch data from one or more columns of a table.

My Notes


---


---


---


---

2. WHERE Clause

Simple Definition

WHERE filters rows based on a condition.

Why it is Used

Retrieve specific records

Reduce unwanted data

Apply conditions


Syntax

SELECT column_name
FROM table_name
WHERE condition;

Examples

Example 1

SELECT *
FROM Employees
WHERE Department='IT';

Example 2

SELECT *
FROM Employees
WHERE Salary > 60000;

Example 3

SELECT *
FROM Employees
WHERE City='Hyderabad';

Example 4

SELECT Emp_Name, Salary
FROM Employees
WHERE Experience >= 5;

Example 5

SELECT *
FROM Employees
WHERE Department='Finance';

Important Points

WHERE filters rows.

Conditions must evaluate to TRUE.

Strings should be enclosed in quotes.


Common Mistakes

❌ Missing quotes

WHERE Department = IT

❌ Using column alias in WHERE

Short Summary

WHERE helps retrieve only the required rows.

My Notes


---


---


---


---

3. Arithmetic Operators

Simple Definition

Arithmetic operators perform mathematical calculations.

Why it is Used

Calculate totals

Calculate increments

Generate reports


Operators

Operator	Meaning

+	Addition
-	Subtraction
*	Multiplication
/	Division


Syntax

SELECT column1 + column2
FROM table_name;

Examples

Example 1

SELECT Salary + Bonus
FROM Employees;

Example 2

SELECT Salary - 2000
FROM Employees;

Example 3

SELECT Salary * 12
FROM Employees;

Example 4

SELECT Salary / 2
FROM Employees;

Example 5

SELECT Emp_Name,
       Salary + 5000
FROM Employees;

Important Points

Arithmetic operations can be performed on numeric columns.

NULL in calculations often returns NULL.


Common Mistakes

❌ Using arithmetic operators on text data.

❌ Ignoring NULL values.

Short Summary

Arithmetic operators help perform calculations in SQL queries.

My Notes


---


---


---


---

4. Comparison Operators

Simple Definition

Comparison operators compare values.

Why it is Used

Filter data

Compare numeric values

Compare text values


Operators

Operator	Meaning

=	Equal
>	Greater Than
<	Less Than
>=	Greater Than or Equal
<=	Less Than or Equal
<>	Not Equal


Syntax

SELECT *
FROM table_name
WHERE condition;

Examples

Example 1

SELECT *
FROM Employees
WHERE Salary = 50000;

Example 2

SELECT *
FROM Employees
WHERE Salary > 60000;

Example 3

SELECT *
FROM Employees
WHERE Experience < 5;

Example 4

SELECT *
FROM Employees
WHERE Department <> 'IT';

Example 5

SELECT *
FROM Employees
WHERE Salary >= 65000;

Important Points

Used mainly with WHERE.

Can compare numbers and strings.


Common Mistakes

❌ Using == instead of =

WHERE Salary == 50000

Short Summary

Comparison operators are used to compare values and filter records.

My Notes


---


---


---


---

5. Logical Operators

Simple Definition

Logical operators combine multiple conditions.

Why it is Used

Apply multiple filters

Build complex conditions


Operators

Operator	Meaning

AND	All conditions true
OR	Any condition true
NOT	Opposite condition


Syntax

SELECT *
FROM table_name
WHERE condition1 AND condition2;

Examples

Example 1

SELECT *
FROM Employees
WHERE Department='IT'
AND Salary > 60000;

Example 2

SELECT *
FROM Employees
WHERE Department='HR'
OR Department='Finance';

Example 3

SELECT *
FROM Employees
WHERE NOT Department='Sales';

Example 4

SELECT *
FROM Employees
WHERE City='Bangalore'
AND Experience > 5;

Example 5

SELECT *
FROM Employees
WHERE Salary > 50000
OR Experience > 8;

Important Points

AND narrows results.

OR increases results.

NOT reverses conditions.


Common Mistakes

❌ Incorrect condition grouping.

❌ Forgetting logical operators between conditions.

Short Summary

Logical operators help combine multiple conditions.

My Notes


---


---


---


---

6. NULL Handling

Simple Definition

NULL represents missing or unknown data.

Why it is Used

Handle incomplete data

Identify missing values


Syntax

WHERE column IS NULL

WHERE column IS NOT NULL

Examples

Example 1

SELECT *
FROM Employees
WHERE Bonus IS NULL;

Example 2

SELECT *
FROM Employees
WHERE Bonus IS NOT NULL;

Example 3

SELECT Emp_Name
FROM Employees
WHERE Bonus IS NULL;

Example 4

SELECT *
FROM Employees
WHERE Bonus IS NOT NULL;

Example 5

SELECT Emp_Name, Bonus
FROM Employees
WHERE Bonus IS NULL;

Important Points

NULL is not zero.

NULL is not an empty string.

Use IS NULL or IS NOT NULL.


Common Mistakes

❌

WHERE Bonus = NULL

Correct:

WHERE Bonus IS NULL

Short Summary

NULL handling helps identify missing values correctly.

My Notes


---


---


---


---

Part 2 – Practice Workbook (3 Hours)

Section A – Fill in the Blanks (Easy)

1. __________ statement is used to retrieve data from a table.


2. The __________ clause is used to filter rows.


3. The symbol * in SELECT means __________.


4. The operator > means __________.


5. The operator <> means __________.


6. AND returns TRUE only when __________ conditions are TRUE.


7. OR returns TRUE when __________ condition is TRUE.


8. NULL represents __________ data.


9. To check NULL values we use __________ NULL.


10. To check non-NULL values we use __________ NOT NULL.




---

Section B – True or False (Easy)

1. SELECT is used to delete data.


2. WHERE filters rows.


3. NULL and 0 are the same.


4. AND combines multiple conditions.


5. OR requires all conditions to be TRUE.


6. Comparison operators are used with WHERE.


7. Bonus = NULL is the correct syntax.


8. SELECT * returns all columns.


9. Arithmetic operators can perform calculations.


10. NOT reverses a condition.




---

Section C – Match the Following (Easy)

Column A	Column B

SELECT	Missing Value
WHERE	Retrieve Data
NULL	Filter Data
AND	Addition
+	Multiple Conditions



---

Section D – Short Answer Questions (Easy)

1. What is the purpose of SELECT?


2. What is the use of WHERE clause?


3. What is NULL?


4. Name any four comparison operators.


5. What is the difference between AND and OR?


6. Why do we use arithmetic operators?


7. What does SELECT * do?


8. What is IS NULL used for?




---

Section E – Predict the Output (Medium)

1. 

SELECT Emp_Name
FROM Employees
WHERE Department='IT';

2. 

SELECT Emp_Name
FROM Employees
WHERE Salary > 70000;

3. 

SELECT Emp_Name
FROM Employees
WHERE Bonus IS NULL;

4. 

SELECT Emp_Name
FROM Employees
WHERE Department='HR'
AND Experience > 2;

5. 

SELECT Emp_Name
FROM Employees
WHERE City='Chennai'
OR Salary > 70000;

6. 

SELECT Salary * 12
FROM Employees
WHERE Emp_ID=101;

7. 

SELECT Emp_Name
FROM Employees
WHERE Department <> 'Sales';

8. 

SELECT Emp_Name
FROM Employees
WHERE NOT City='Bangalore';


---

Section F – Write SQL Queries (Medium)

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


15. Display employee name and salary after adding ₹5000.




---

Section G – Find the Error (Debug SQL) (Difficult)

1. 

SELECT FROM Employees;

2. 

SELECT Emp_Name Salary
Employees;

3. 

SELECT *
FROM Employees
WHERE Department = IT;

4. 

SELECT *
FROM Employees
WHERE Salary >> 50000;

5. 

SELECT *
FROM Employees
WHERE Bonus = NULL;

6. 

SELECT *
FROM Employees
WHERE Department='IT'
Salary > 60000;

7. 

SELECT *
Employees
WHERE Salary > 50000;

8. 

SELECT *
FROM Employees
WHERE Experience => 5;


---

Section H – Mini Assessment (Difficult)

1. Write a query to display employees from Bangalore whose salary is greater than 65000.


2. Write a query to display employees from Hyderabad or Pune.


3. Write a query to display employees with salary between 50000 and 65000 using logical operators.


4. Write a query to display employees whose bonus is missing.


5. Write a query to display employees whose department is not HR.


6. Write a query to display employee name and annual salary.


7. Write a query to display employees with experience greater than 5 years and salary greater than 60000.


8. Predict the output:



SELECT Emp_Name
FROM Employees
WHERE Bonus IS NOT NULL
AND Salary > 55000;

9. Predict the output:



SELECT Emp_Name
FROM Employees
WHERE Department='IT'
OR Department='Finance';

10. Write a query to display employees whose city is Chennai and bonus is not NULL.




---

End of Day 2 Student Notes + 3-Hour Practice Workbook
