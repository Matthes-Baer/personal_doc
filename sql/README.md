# SQL

This section covers information about the programming language Rust.

## Useful Links
- [Learn Basic SQL](https://www.youtube.com/watch?v=kbKty5ZVKMY)


## General Information
- SQL (Structured Query Language) is used to communicate with relational databases like MySQL, PostgreSQL, SQL Server, SQLite, Oracle, etc.
- SQL is case-insensitive (SELECT = select), but it's common practice to write keywords in uppercase for readability.
- Always use `WHERE` with `UPDATE` and `DELETE` to avoid affecting all rows.
- Use indexes for performance (on columns used in `JOIN`, `WHERE`, `ORDER BY`).
- Prefer parameterized queries to avoid SQL injection (especially in applications).
- Always back up your data before running large `UPDATE` or `DELETE`.
- SQL string functions are usually 1-indexed, meaning: The first character in a string is position 1, not 0.
  - `SELECT SUBSTRING('OpenAI', 1, 2);  -- Output: 'Op'`


## Important SQL Commands/Clauses/Expressions

- `SELECT` - Retrieve data from a database
- `INSERT` - Add new data to a database
- `UPDATE` - Modify existing data in a database
- `DELETE` - Remove data from a database
- `CREATE` - Create new tables or databases
- `ALTER` - Modify existing table structures
- `DROP` - Delete tables or databases

- `WHERE` - Filter records based on conditions
- `GROUP BY` - Aggregate data based on one or more columns
- `ORDER BY` - Sort records in ascending or descending order
- `HAVING` - Filters aggregated data
- `JOIN` (this is an alias/short version for `INNER JOIN`) - Combines rows from two or more tables based on a related column. Think of it as an intersection: "Give me only the things that exist in both."
  - `LEFT JOIN` - Returns all records from the left table and matched records from the right table
  - `RIGHT JOIN` - Returns all records from the right table and matched records from the left table
  - `FULL OUTER JOIN` - All records from both tables, with NULLs for non-matching rows
  - `CROSS JOIN` - Cartesian product of two tables, combining all rows from both tables
    - A Cartesian product occurs when you combine every row from one table with every row from another table — essentially all possible combinations of rows between the two tables.
- `LIMIT` / `OFFSET` - Control the number of records returned
- `IN` - Check if a value exists in a set
- `LIKE` - Search for a specified pattern in a column
- `BETWEEN` - Allows filtering of records within a range
- `IS NULL` - Check for NULL values in a column
- `CASE` - SQL's way of handling conditional logic, similar to `if-else` statements in programming languages


## Functions
- `LEFT(string, number)` - Returns the leftmost number of characters from a string
  - `SELECT LEFT('OpenAI', 4);  -- Output: 'Open'`
- `RIGHT(string, number)` - Returns the rightmost number of characters from a string
  - `SELECT RIGHT('OpenAI', 2);  -- Output: 'AI'`
- `RTRIM` - Removes trailing spaces from a string
  - `SELECT RTRIM('OpenAI   ');  -- Output: 'OpenAI'`
- `LTRIM` - Removes leading spaces from a string
 - `SELECT LTRIM('   OpenAI');  -- Output: 'OpenAI'`
- `LPAD(string, length, pad_string)` - Left-pads a string with a specified character to a certain length
  - `SELECT LPAD('OpenAI', 10, '*');  -- Output: '****OpenAI'`
- `RPAD(string, length, pad_string)` - Right-pads a string with a specified character to a certain length
  - `SELECT RPAD('AI', 5, '*');  -- Output: 'AI***'`
- `SUBSTRING(string, start, length)` - Extracts a substring
  - `SELECT SUBSTRING('OpenAI', 2, 3);  -- Output: 'pen'`
- `TRIM([LEADING | TRAILING | BOTH] trim_character FROM string)` - Removes characters (default is spaces) from a string
  - `SELECT TRIM(BOTH 'x' FROM 'xxxOpenAIxxx');  -- Output: 'OpenAI'`
- `CONCAT(string1, string2, ...)` - Joins multiple strings into one
  - `SELECT CONCAT('Open', 'AI');  -- Output: 'OpenAI'`
- `REPLACE(string, from_substring, to_substring)` - Replaces occurrences of a substring in a string with another substring
  - `SELECT REPLACE('OpenAI GPT', 'OpenAI', 'ChatGPT');  -- Output: 'ChatGPT GPT'`
- `LENGTH(string)` - Returns the number of characters (or bytes, depending on SQL dialect) in a string. In some databases (like MySQL), `LENGTH()` returns the number of bytes, and `CHAR_LENGTH()` or `CHARACTER_LENGTH()` returns the number of characters, especially important for multibyte characters like emojis or accented characters.
  - `SELECT LENGTH('OpenAI');  -- Output: 6`
- `LOCATE(substring, string [, start]) (MySQL)` or `POSITION(substring IN string) (ANSI SQL)` - Returns the position (1-based index) of the first occurrence of a substring in a string. If the substring is not found, it returns 0.
  - `SELECT LOCATE('AI', 'OpenAI');  -- Output: 5`
  - `SELECT POSITION(' ' IN 'Hello World');  -- Output: 6`
- `UPPER(string)` - Converts a string to uppercase
  - `SELECT UPPER('OpenAI');  -- Output: 'OPENAI'`
- `LOWER(string)` - Converts a string to lowercase
  - `SELECT LOWER('OpenAI');  -- Output: 'openai'`


## Code Examples

### Select Specific Columns

```sql
SELECT first_name, last_name FROM employees;
```

### Filter Records

```sql
SELECT * FROM orders
WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31'
  AND status = 'shipped';
```

### Aggregate Data

Goal: Count how many employees are in each department.

`GROUP BY department`: Groups rows with the same department value together.
`COUNT(*)`: Counts how many rows are in each group.
`AS employee_count`: Gives the result column a readable name.

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```

### Sort Results

```sql
SELECT * FROM products
ORDER BY price DESC
LIMIT 10;
```

### JOIN Two Tables

Goal: Show each order’s ID, total amount, and the customer’s name.

`JOIN customers c`: Combines the orders table with the customers table.
`ON o.customer_id = c.customer_id`: Tells SQL how the tables are related — the customer_id is the key that links them.
Aliases: o and c are table aliases to shorten table names.

The `JOIN` / `INNER JOIN` Keeps only matching rows between the two tables.
If a row in orders has no matching customer_id in customers, it won’t show up.
Think of it as an intersection: "Give me only the things that exist in both."

```sql
SELECT o.order_id, c.name, o.total
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;
```

### LEFT JOIN for Missing Data

The `LEFT JOIN` keeps all rows from the "left" table (employees), and fills in data from the "right" table (departments) if there’s a match. If there's no matching department, the department_name will be NULL. This is the same for `RIGHT JOIN` but vice versa. `FULL OUTER JOIN` would be basically the combination of both, keeping all records from both tables while filling in NULL on both sides if no matches occur.

Use Case: You want to see all employees, even those who aren't assigned to a department.

```sql
SELECT e.name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.id;
```

### Subquery

```sql
SELECT name, salary
FROM employees
WHERE salary > (
  SELECT AVG(salary) FROM employees
);
```

### Update Records

```sql
UPDATE products
SET price = price * 1.10
WHERE category = 'electronics';
```

### Delete Rows Carefully

```sql
DELETE FROM users
WHERE last_login < '2022-01-01';
```

### Create Table

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(255) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Index for Performance

Goal: Speed up queries that search or join using the customer_id column in the orders table.

`CREATE INDEX`: Builds a lookup structure for faster access (like a book’s index).
`ON orders(customer_id)`: Specifies the table and column to index.
`idx_orders_customer`: Is the name of the index (can be anything descriptive).

Note: Indexes speed up reads, but slow down writes (INSERT/UPDATE/DELETE) slightly, so use them wisely.

```sql
CREATE INDEX idx_orders_customer ON orders(customer_id);
```

### Find Duplicates

Goal: Identify email addresses that appear more than once in the users table.

`GROUP BY email`: Groups rows with the same email.
`COUNT(*)`: Counts how many times each email appears.
`HAVING COUNT(*) > 1`: Filters the results to only show duplicates (i.e., emails that appear more than once).

```sql
SELECT email, COUNT(*)
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

### Window Function (Running Total)

Goal: Calculate the running total of order amounts for each customer over time.

`SUM(total)`: Adds up the order amounts.
`OVER (...)`: Turns the aggregation into a window function.
`PARTITION BY customer_id`: Restarts the total for each customer.
`ORDER BY order_date`: Ensures totals build over time (chronologically).
`running_total`: Shows cumulative spending per customer.

A Window Function lets you perform calculations across a set of rows that are "related" to the current row, but without collapsing the rows like `GROUP BY` does.

```sql
SELECT
  customer_id,
  order_date,
  total,
  SUM(total) OVER (PARTITION BY customer_id ORDER BY order_date) AS running_total
FROM orders;
```

### Debugging Performances Issues

```sql
EXPLAIN SELECT * FROM orders WHERE customer_id = 5;
```

### Usage of Wildcards

This works with `LIKE` but not for `IN` as it expects exact matches.

```sql
SELECT * FROM products
WHERE name LIKE 'Apple%';  -- Finds products starting with 'Apple'
```

```sql
SELECT * FROM users
WHERE name LIKE '%lise%'; -- Contains 'lise' anywhere in the name
```

```sql
SELECT * FROM users
WHERE name LIKE '%lise'; -- Ends with 'lise'
```

```sql
SELECT * FROM users
WHERE LOWER(name) LIKE 'elise%'; -- case-insensitive search, starting with 'elise' / use `ILIKE` in PostgreSQL
```

```sql
SELECT * FROM users
WHERE name LIKE 'T_some'; -- Finds names like 'T_some', where '_' matches any single character (using % would match any number of characters)
```

### CASE Statement

Suppose you have a students table with a score column and want to assign grades:

```sql
SELECT name, score,
    CASE
        WHEN score >= 90 THEN 'A'
        WHEN score >= 80 THEN 'B'
        WHEN score >= 70 THEN 'C'
        ELSE 'F'
    END AS grade
FROM students;
```

The first `WHEN` that evaluates to `TRUE` is used.
`ELSE` is optional but recommended for clarity and completeness.

### Create a function and trigger in SQL (mariaDB)

`DELIMITER` is necessary within heidiSQL query editor, but when you use it in code with `execute` or `addSql` (within a migration e.g.), you mustn't use `DELIMITER` (at least with MikroORM)

```sql
-- Create a function
DELIMITER //

CREATE OR REPLACE FUNCTION abc(a_id VARCHAR(255))
RETURNS INT
DETERMINISTIC
BEGIN
  DECLARE something INT;

  SELECT COUNT(*) INTO something
  FROM some_table
  WHERE id = a_id

  RETURN something
END //

DELIMITER ;

-- use the function later on:
SELECT abc("123")


-- Use DROP FUNCTION abc to delete a function
```

```sql
-- Create a trigger to execute the function
CREATE OR REPLACE TRIGGER some_trigger
AFTER UPDATE OF a ON b_table
FOR EACH ROW
EXECUTE FUNCTION abc("abc");

-- Use DROP TRIGGER some_trigger to delete a trigger
```


### Add trigger in Nest.js/MikroORM migration manually

The following adds special triggers to BEFORE INSERT and BEFORE UPDATE on a table - this checks on database-level for specific constraints instead of having such checks only on application-level. Currently (03.10.25), MikroORM is not providing a better approach to using triggers besides adding them manually via a manual created migration.
`NEW` is special and is resolved with the inserted/updated entry during the insert/update process.

```ts
...

override async up(): Promise<void> {
  this.addSql(`CREATE OR REPLACE TRIGGER abc_insert
  BEFORE INSERT ON some_table
  FOR REACH ROW
  BEGIN
    IF EXISTS (... WHERE a.name = NEW.name)
    THEN
    SIGNAL SQLSTATE '45000'
      SET MESSAGE_TEXT = 'already exists'
    END IF
  END;`)

  this.addSql(`CREATE OR REPLACE TRIGGER abc_update
  BEFORE UPDATE ON some_table
  FOR REACH ROW
  BEGIN
    IF EXISTS (... WHERE a.name = NEW.name)
    THEN
    SIGNAL SQLSTATE '45000'
      SET MESSAGE_TEXT = 'already exists'
    END IF
  END;`)
}

override async down(): Promise<void> {
  this.addSql(`DROP TRIGGER IF EXISTS abc_insert;`)
  this.addSql(`DROP TRIGGER IF EXISTS abc_update;`)
}
```
