# SQL Learning Guide

This project is designed to help you learn SQL using practical examples and exercises.

## Why MySQL?

- MySQL is open-source.
- MySQL is free.
- MySQL is ideal for both small and large applications.
- MySQL is very fast, reliable, scalable, and easy to use.

## SELECT Statement

#### The `SELECT` statement is used to select data from a database.

### SELECT Syntax

#### Select Specific Columns:

```sql
SELECT column1, column2, ...
FROM table_name;
```
Example:

```sql 
SELECT CustomerName, City, Country FROM Customers;
```
#### Select All Columns:
```sql
SELECT * FROM table_name;
```
Example:
```sql
SELECT * FROM Customers;
```
## SELECT DISTINCT
#### The SELECT `DISTINCT` statement is used to return only distinct (different) values.
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
Example:
```sql
SELECT DISTINCT Country FROM Customers;
```
 retrieves a list of **unique values** from the "Country" column in the "Customers" table.
 <br> <br> <br>
## WHERE Clause
#### The `WHERE` clause is used to filter records.

Operators in The WHERE Clause:
| Operator | Description                                           |                                   
|----------|-------------------------------------------------------|
| =        | Equal                                                 |
| >        | Greater than                                          |                                               |
| <        | Less than                                             |                                               |
| >=       | Greater than or equal                                 |                                               |
| <=       | Less than or equal                                    |                                               |
| <>       | Not equal. In some versions of SQL this operator may be written as !=                                             |
| BETWEEN  | Between a certain range                               |                                               |
| LIKE     | Search for a pattern                                  |                                               |
| IN       | To specify multiple possible values for a column      |                                               |

Example:
```sql
SELECT * FROM Customers WHERE Country = 'Mexico';
SELECT * FROM Customers WHERE NOT Country = 'Germany';
```
 <br>
 
## **ORDER BY** Keyword
#### The `ORDER` BY keyword is used to sort the result-set in ascending or descending order.
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```
Example:
```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

## NULL Values
#### Use **IS NULL** and **IS NOT NULL** operators to filter records with NULL values.
```sql
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```
Example:
```sql
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NULL;
```

## LIMIT Clause
#### The **LIMIT** clause is used to specify the number of records to return.
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```
## Aggregate Functions


| Function | Description                                            |
|----------|--------------------------------------------------------|
| MIN()    | Returns the smallest value of the selected column.     |
| MAX()    | Returns the largest value of the selected column.      |
| COUNT()  | Returns the number of rows that match a specified criterion. |
| SUM()    | Returns the total sum of a numeric column.             |
| AVG()    | Returns the average value of a numeric column.         |


Example:<br>

```sql
SELECT MAX(Price)  FROM Products;
```
## LIKE Operator
#### The **LIKE** operator is used in a WHERE clause to search for a specified pattern in a column.

#### There are two wildcards often used in conjunction with the LIKE operator:
* The percent sign (%) represents zero, one, or multiple characters.<br>
* The underscore sign (_) represents one single character.

<br>

| LIKE Pattern              | Description                                                    |
|---------------------------|----------------------------------------------------------------|
| WHERE CustomerName LIKE 'a%'  | Finds any values that start with "a".                            |
| WHERE CustomerName LIKE '%a'  | Finds any values that end with "a".                              |
| WHERE CustomerName LIKE '%or%' | Finds any values that have "or" in any position.                |
| WHERE CustomerName LIKE '_r%'  | Finds any values that have "r" in the second position.           |
| WHERE CustomerName LIKE 'a_%'  | Finds any values that start with "a" and are at least 2 characters in length. |
| WHERE CustomerName LIKE 'a__%' | Finds any values that start with "a" and are at least 3 characters in length. |
| WHERE ContactName LIKE 'a%o'   | Finds any values that start with "a" and ends with "o".         |

<br>


## IN Operator
#### The **IN** operator allows you to specify multiple values in a WHERE clause.

```sql
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');
```
```sql
SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers);
```
## Aliases
Aliases are used to give a table, or a column in a table, a temporary name. An alias is created with the AS keyword.

```sql
SELECT CustomerName AS Customer, ContactName AS "Contact Person"
FROM Customers;
```
## CONCAT Function
The **CONCAT** function is used to concatenate two or more strings.
```sql
SELECT CONCAT(firstName, " ", lastName) AS fullname
FROM Customers;
```
## Fetch
#### FETCH clause skips N rows in a result set before starting to return any rows.
```sql
OFFSET offset_rows { ROW | ROWS }
FETCH { FIRST | NEXT } [ fetch_rows ] { ROW | ROWS } ONLY
```
Exmaple:
```sql
SELECT * FROM employees
ORDER BY 
    salary DESC
OFFSET 5 ROWS
FETCH NEXT 5 ROWS ONLY;
```
##### it skips the first 5 rows using the OFFSET clause and fetches the next 5 rows using the FETCH NEXT clause.
<br>

## SQL ALL Operator
| Condition   | Meaning                                                                                  |
|-------------|------------------------------------------------------------------------------------------|
| c > ALL(…)  | The values in column c must be greater than the biggest value in the set to evaluate to true. |
| c >= ALL(…) | The values in column c must be greater than or equal to the biggest value in the set to evaluate to true. |
| c < ALL(…)  | The values in column c must be less than the lowest value in the set to evaluate to true. |
| c <= ALL(…) | The values in column c must be less than or equal to the lowest value in the set to evaluate to true. |
| c <> ALL(…) | The values in column c must not be equal to any value in the set to evaluate to true.    |
| c = ALL(…)  | The values in column c must be equal to any value in the set to evaluate to true.        |


Example:
```sql
SELECT 
    first_name, last_name, salary
FROM
    employees
WHERE
    salary > ALL (SELECT 
            salary
        FROM
            employees
        WHERE
            department_id = 2)
ORDER BY salary;
```


##  SQL ANY Operator
| Condition    | Meaning                                                                                  |
|--------------|------------------------------------------------------------------------------------------|
| x = ANY (…)  | The values in column x must match one or more values in the set to evaluate to true.      |
| x != ANY (…) | The values in column x must not match one or more values in the set to evaluate to true.  |
| x > ANY (…)  | The values in column x must be greater than the smallest value in the set to evaluate to true. |
| x < ANY (…)  | The values in column x must be smaller than the biggest value in the set to evaluate to true. |
| x >= ANY (…) | The values in column x must be greater than or equal to the smallest value in the set to evaluate to true. |
| x <= ANY (…) | The values in column x must be smaller than or equal to the biggest value in the set to evaluate to true. |


Example:
```sql
SELECT * FROM table_name WHERE column_x = ANY (1, 2, 3);

```
The values in column x must match one or more values in the set to evaluate to true.


## SQL EXISTS Operator

The EXISTS keyword in SQL is used in a WHERE clause to check for the existence of rows returned by a subquery. It returns true if the subquery returns one or more rows, and false otherwise.
```sql
SELECT *
FROM customers c
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.customer_id
);
```

## SQL CASE Expression

#### The SQL CASE expression allows you to evaluate a list of conditions and returns one of the possible results. 
### Simple CASE expression:
``` sql
SELECT 
    first_name,
    last_name,
    hire_date,
    CASE (2000 - YEAR(hire_date))
        WHEN 1 THEN '1 year'
        WHEN 3 THEN '3 years'
        WHEN 5 THEN '5 years'
        WHEN 10 THEN '10 years'
    END aniversary
FROM
    employees
ORDER BY first_name;
```

### Searched CASE Expression:
```sql
SELECT 
    first_name,
    last_name,
    CASE
        WHEN salary < 3000 THEN 'Low'
        WHEN salary >= 3000 AND salary <= 5000 THEN 'Average'
        WHEN salary > 5000 THEN 'High'
    END evaluation
FROM
    employees;
```
