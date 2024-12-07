# SQL Commands Guide

## Basic Queries

| Command         | Description                                      | Example                                      |
|-----------------|--------------------------------------------------|----------------------------------------------|
| `SELECT`        | Retrieves data from a database                   | `SELECT * FROM users;`                       |
| `INSERT`        | Inserts new data into a database                 | `INSERT INTO users (name, age) VALUES ('John', 30);` |
| `UPDATE`        | Updates existing data within a table             | `UPDATE users SET age = 31 WHERE name = 'John';` |
| `DELETE`        | Deletes data from a database                     | `DELETE FROM users WHERE name = 'John';`     |
| `CREATE TABLE`  | Creates a new table in the database              | `CREATE TABLE users (id INT, name VARCHAR(100), age INT);` |
| `DROP TABLE`    | Deletes a table from the database                | `DROP TABLE users;`                          |

## Filters

| Command         | Description                                      | Example                                      |
|-----------------|--------------------------------------------------|----------------------------------------------|
| `WHERE`         | Filters records based on a condition             | `SELECT * FROM users WHERE age > 25;`        |
| `LIKE`          | Searches for a specified pattern in a column     | `SELECT * FROM users WHERE name LIKE 'J%';`  |
| `IN`            | Checks if a value matches any value in a list    | `SELECT * FROM users WHERE age IN (25, 30);` |
| `BETWEEN`       | Selects values within a given range              | `SELECT * FROM users WHERE age BETWEEN 20 AND 30;` |
| `IS NULL`       | Checks for null values                           | `SELECT * FROM users WHERE email IS NULL;`   |

## Joins

| Command         | Description                                      | Example                                      |
|-----------------|--------------------------------------------------|----------------------------------------------|
| `INNER JOIN`    | Returns records that have matching values in both tables | `SELECT users.name, orders.amount FROM users INNER JOIN orders ON users.id = orders.user_id;` |
| `LEFT JOIN`     | Returns all records from the left table, and the matched records from the right table | `SELECT users.name, orders.amount FROM users LEFT JOIN orders ON users.id = orders.user_id;` |
| `RIGHT JOIN`    | Returns all records from the right table, and the matched records from the left table | `SELECT users.name, orders.amount FROM users RIGHT JOIN orders ON users.id = orders.user_id;` |
| `FULL JOIN`     | Returns all records when there is a match in either left or right table | `SELECT users.name, orders.amount FROM users FULL JOIN orders ON users.id = orders.user_id;` |

## Aggregate Functions

| Command         | Description                                      | Example                                      |
|-----------------|--------------------------------------------------|----------------------------------------------|
| `COUNT`         | Returns the number of rows that matches a specified criterion | `SELECT COUNT(*) FROM users;`               |
| `SUM`           | Returns the total sum of a numeric column        | `SELECT SUM(amount) FROM orders;`            |
| `AVG`           | Returns the average value of a numeric column    | `SELECT AVG(age) FROM users;`                |
| `MIN`           | Returns the smallest value of the selected column| `SELECT MIN(age) FROM users;`                |
| `MAX`           | Returns the largest value of the selected column | `SELECT MAX(age) FROM users;`                |
| `GROUP BY`      | Groups rows that have the same values            | `SELECT COUNT(*), age FROM users GROUP BY age;` |
| `HAVING`        | Filters groups based on a condition              | `SELECT COUNT(*), age FROM users GROUP BY age HAVING COUNT(*) > 1;` |

## Operators

| Operator        | Description                                      | Example                                      |
|-----------------|--------------------------------------------------|----------------------------------------------|
| `=`             | Equal to                                         | `SELECT * FROM users WHERE age = 30;`        |
| `<>` or `!=`    | Not equal to                                     | `SELECT * FROM users WHERE age <> 30;`       |
| `>`             | Greater than                                     | `SELECT * FROM users WHERE age > 30;`        |
| `<`             | Less than                                        | `SELECT * FROM users WHERE age < 30;`        |
| `>=`            | Greater than or equal to                         | `SELECT * FROM users WHERE age >= 30;`       |
| `<=`            | Less than or equal to                            | `SELECT * FROM users WHERE age <= 30;`       |

## Booleans

| Operator        | Description                                      | Example                                      |
|-----------------|--------------------------------------------------|----------------------------------------------|
| `AND`           | Combines two or more conditions                  | `SELECT * FROM users WHERE age > 25 AND name = 'John';` |
| `OR`            | Combines two or more conditions                  | `SELECT * FROM users WHERE age > 25 OR name = 'John';`  |
| `NOT`           | Negates a condition                              | `SELECT * FROM users WHERE NOT age = 30;`    |

## Constraints

| Constraint      | Description                                      | Example                                      |
|-----------------|--------------------------------------------------|----------------------------------------------|
| `PRIMARY KEY`   | Uniquely identifies each record in a table       | `CREATE TABLE users (id INT PRIMARY KEY, name VARCHAR(100));` |
| `FOREIGN KEY`   | Uniquely identifies a record in another table    | `CREATE TABLE orders (id INT, user_id INT, FOREIGN KEY (user_id) REFERENCES users(id));` |
| `UNIQUE`        | Ensures all values in a column are unique        | `CREATE TABLE users (id INT, email VARCHAR(100) UNIQUE);` |
| `NOT NULL`      | Ensures a column cannot have a NULL value        | `CREATE TABLE users (id INT, name VARCHAR(100) NOT NULL);` |
| `CHECK`         | Ensures all values in a column satisfy a specific condition | `CREATE TABLE users (id INT, age INT CHECK (age >= 18));` |
| `DEFAULT`       | Sets a default value for a column if no value is specified | `CREATE TABLE users (id INT, created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP);` |