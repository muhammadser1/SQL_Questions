# SQL Learning Guide

This project is designed to help you learn SQL using practical examples and exercises.

## Why MySQL?

- MySQL is open-source.
- MySQL is free.
- MySQL is ideal for both small and large applications.
- MySQL is very fast, reliable, scalable, and easy to use.

## SELECT Statement

The `SELECT` statement is used to select data from a database:

```sql
SELECT * FROM table_name;
SELECT CustomerName, City, Country FROM Customers;

The SELECT DISTINCT statement is used to return only distinct (different) values:

The SELECT DISTINCT statement is used to return only distinct (different) values:

sql
Copy code
SELECT DISTINCT Country FROM Customers;
WHERE Clause
The WHERE clause is used to filter records.

Operators in The WHERE Clause:
Operator	Description	Example
=	Equal	SELECT * FROM Customers WHERE Country = 'Mexico';
>	Greater than	
<	Less than	
>=	Greater than or equal	
<=	Less than or equal	
<>	Not equal. In some versions of SQL this operator may be written as !=	
BETWEEN	Between a certain range	
LIKE	Search for a pattern	
IN	To specify multiple possible values for a column	
sql
Copy code
SELECT * FROM Customers WHERE Country = 'Mexico';
SELECT * FROM Customers WHERE NOT Country = 'Germany';
ORDER BY Keyword
The ORDER BY keyword is used to sort the result-set in ascending or descending order.

sql
Copy code
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;

SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
NULL Values
Use IS NULL and IS NOT NULL operators to filter records with NULL values.

sql
Copy code
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
MySQL LIMIT Clause
The LIMIT clause is used to specify the number of records to return.

sql
Copy code
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
Aggregate Functions
The MIN() function returns the smallest value of the selected column.
The MAX() function returns the largest value of the selected column.
The COUNT() function returns the number of rows that matches a specified criterion.
The SUM() function returns the total sum of a numeric column.
The AVG() function returns the average value of a numeric column.
sql
Copy code
SELECT MAX(Price) AS LargestPrice FROM Products;
LIKE Operator
The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

There are two wildcards often used in conjunction with the LIKE operator:

The percent sign (%) represents zero, one, or multiple characters.
The underscore sign (_) represents one single character.
LIKE Operator Examples
LIKE Pattern	Description
WHERE CustomerName LIKE 'a%'	Finds any values that start with "a"
WHERE CustomerName LIKE '%a'	Finds any values that end with "a"
WHERE CustomerName LIKE '%or%'	Finds any values that have "or" in any position
WHERE CustomerName LIKE '_r%'	Finds any values that have "r" in the second position
WHERE CustomerName LIKE 'a_%'	Finds any values that start with "a" and are at least 2 characters in length
WHERE CustomerName LIKE 'a__%'	Finds any values that start with "a" and are at least 3 characters in length
WHERE ContactName LIKE 'a%o'	Finds any values that start with "a" and ends with "o"
The MySQL IN Operator
The IN operator allows you to specify multiple values in a WHERE clause.

sql
Copy code
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');

SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers);
MySQL Aliases
Aliases are used to give a table, or a column in a table, a temporary name. An alias is created with the AS keyword.

sql
Copy code
SELECT CustomerName AS Customer, ContactName AS "Contact Person"
FROM Customers;
CONCAT Function
The CONCAT function is used to concatenate two or more strings.

sql
Copy code
SELECT CONCAT(firstName, " ", lastName) AS fullname
FROM Customers;
perl
