## What is a database?

A database is a collection of interrelated data that is stored in an organized manner for easy access, management, and maintenance. Each table consists of rows and columns to store data. A database can be defined as a structured form of data storage from which data can be retrieved and managed based on requirements.

## What is SQL?

SQL stands for Structured Query Language. It uses SQL queries to interact with the database, i.e., to create a database, to create a table in the database, to retrieve data or update a table in the database, etc.

## Main Data Types in SQL

| Data Types          | Definition               | Syntax             |
|---------------------|--------------------------|--------------------|
| INT (integer)       | Used for whole numbers   | `CREATE TABLE Employees (ID INT, Name VARCHAR(30));` |
| FLOAT (floating point number) | Used for decimal and fractional numbers | `CREATE TABLE Item (ID INT, Price Decimal(5,2));` |
| CHAR (fixed-length character string) | Used for fixed-length strings | `CREATE TABLE Employees (ID INT, initial CHAR(1));` |
| VARCHAR (variable-length character string) | Used for variable-length strings | `CREATE TABLE Employees (ID INT, Name VARCHAR(30));` |
| DATE (date)         | Used for dates in the format (YYYY-MM-DD) | `CREATE TABLE Employees (ID INT, BirthDate DATE);` |
| DATETIME (date and time) | Used for date and time values in the format (YYYY-MM-DD HH:MM:SS) | `CREATE TABLE Employees (ID INT, OrderDate DATETIME);` |
| BOOLEAN (true or false) | Used for boolean values | |

## SQL Injection and Prevention

SQL injection is a technique used to exploit user data through web page inputs by injecting SQL commands as statements. These statements can manipulate the application's web server by malicious users.

**Prevention Methods:**
- Using type-safe SQL parameters
- Using parameterized input with stored procedures
- Filtering inputs
- Reviewing codes
- Wrapping parameters

**Common SQL Injection Examples:**
- **Basic Injection:** `' OR '1'='1` in a login form
- **Union-Based:** Adding `UNION SELECT` to retrieve additional data
- **Blind Injection:** Extracting data through true/false responses

## Tables and Fields

Tables are the database objects where data is stored logically. A table is an organized collection of data stored in the form of rows and columns. A row/tuple in a table represents a record, and columns represent the different fields. Fields have data types such as text, dates, numbers, and links.

## Pagination in SQL Queries

Implementing pagination in SQL queries allows you to retrieve and display a subset of results from a larger dataset.

**Syntax:**
```sql
SELECT column1, column2 FROM table_name ORDER BY column1 LIMIT 10 OFFSET 10;
```

## SQL Clause Execution Order (Logical Processing Flow)

1. **FROM/JOIN** (Identify Data Sources)
2. **WHERE** (Row Filtering)
3. **GROUP BY** (Aggregation)
4. **HAVING** (Group Filtering)
5. **SELECT** (Column Selection)
6. **DISTINCT** (Duplicate Removal)
7. **ORDER BY** (Sorting)
8. **OFFSET/FETCH or LIMIT** (Pagination)

**Visual Flowchart:**
`FROM/JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT`

## ACID Properties in SQL

1. **Atomicity:** Any operation performed on the data should be executed either entirely or not executed at all.
2. **Consistency:** Ensures that before and after the transaction, the database must be in a consistent state.
3. **Isolation:** Indicates that transactions are isolated from other transactions.
4. **Durability:** All updates done by transaction must become permanent.

## SQL Query Optimization

- **Indexing:** Improve query performance with appropriate indexes.
- **Limit the Result Set:** Use `LIMIT` to reduce the number of rows returned.
- **Avoid `SELECT *`:** Specify only needed columns.
- **Optimize Joins:** Use efficient join conditions and types.
- **Use `EXISTS` Instead of `IN`:** More efficient for large datasets.
- **Avoid Subqueries:** Use JOINs where possible.
- **Efficient WHERE Clause:** Place conditions early to limit data processed.
- **Parameterize Queries:** Avoid SQL injection and benefit from caching.
- **Regular Maintenance:** Analyze and optimize long-running queries.
- **Use Stored Procedures:** Reduce network traffic and enable query plan caching.

## SQL Data Constraints

| Constraints     | Definition                   | Syntax              |
|-----------------|------------------------------|---------------------|
| NOT NULL        | Ensures column values are not null | `CREATE TABLE Students (ID int NOT NULL, Name varchar(255) NOT NULL, Age int);` |
| UNIQUE          | Ensures all values in a column are unique | `CREATE TABLE Students (ID int NOT NULL UNIQUE, Name varchar(255) NOT NULL, Age int);` |
| CHECK           | Ensures values satisfy conditions | `CREATE TABLE Students (ID int NOT NULL, Name varchar(255) NOT NULL, Age int, CHECK (Age>=18));` |
| PRIMARY KEY     | Uniquely identifies each record | `CREATE TABLE Students (ID int NOT NULL, Name varchar(255) NOT NULL, Age int, PRIMARY KEY (ID));` |
| FOREIGN KEY     | Refers to PRIMARY KEY of another table | `CREATE TABLE Orders (OrderID int NOT NULL, OrderNumber int NOT NULL, ID int, PRIMARY KEY (OrderID), FOREIGN KEY (ID) REFERENCES Students(ID));` |
| DEFAULT         | Provides a default value for a column | `CREATE TABLE Students (ID int NOT NULL, Name varchar(255) NOT NULL, Age int, City varchar(255) DEFAULT 'Unknown');` |

## Subquery in SQL

A subquery (also called an inner query or nested query) is a SQL query embedded within another SQL statement. Subqueries allow you to perform operations in multiple steps by using the result of one query as input for another.

## SQL vs MySQL vs NoSQL

### SQL vs MySQL

| Feature       | SQL                       | MySQL                     |
|--------------|--------------------------|--------------------------|
| Type         | Standard language        | Relational DBMS           |
| Usage        | Querying databases       | Store, modify, delete data|
| Licensing    | Licensed product         | Open-source              |
| Security     | High (enterprise-grade)  | Less reliable (open-source) |
| Connectors   | No connectors            | Supports Workbench tool   |

### SQL vs NoSQL

| Feature       | SQL                       | NoSQL                     |
|--------------|--------------------------|--------------------------|
| Structure    | Relational (schema-based)| Non-relational (flexible)|
| Scaling      | Vertical                 | Horizontal               |
| ACID Compliance | Yes                    | CAP theory               |
| Queries      | Complex queries easy     | Complex queries difficult|
| Speed        | -                        | Faster read/writes       |

## CHAR vs VARCHAR

| CHAR                                 | VARCHAR                                |
|--------------------------------------|----------------------------------------|
| Fixed-length character string        | Variable-length character string       |
| Single or multiple-byte              | Up to 255 bytes                        |
| Used when length is known            | Used when length is unknown            |
| Static memory location               | Dynamic memory location                |

## DELETE vs TRUNCATE vs DROP

| Feature        | Drop                 | Delete                | Truncate              |
|---------------|---------------------|----------------------|-----------------------|
| Removes       | Entire table        | Specific rows        | All rows (data only)  |
| Speed         | Slower              | Slower               | Fastest               |
| Transaction Log | No                 | Logs deleted rows    | Doesn't log           |
| Rollback      | Not possible        | Possible             | Not possible          |
| Type          | DDL                 | DML                  | DDL (in some DB)      |

## Primary Key vs Unique Constraint

| Feature       | Primary Key                    | Unique Constraint             |
|--------------|-------------------------------|-------------------------------|
| NULL Values  | Not allowed                   | Allowed (single NULL)         |
| Quantity per Table | One                      | Multiple                      |
| Index        | Creates clustered index       | Creates non-clustered index   |

## BETWEEN vs IN Operators

| Operator      | Usage Example                   | Purpose                     |
|--------------|--------------------------------|-----------------------------|
| `BETWEEN`    | `WHERE age BETWEEN 20 AND 30`  | Range-based filtering       |
| `IN`         | `WHERE id IN (1, 5, 9)`        | Value-list matching         |

## INNER JOIN vs OUTER JOIN

| Join Type    | Result                          | Use-cases                   |
|-------------|--------------------------------|-----------------------------|
| Inner-Join  | Matching rows only              | When you need exact matches |
| Outer-Join  | All rows + NULLs for non-matches | Preserving all records      |

## SQL Keys

| Keys         | Definition                                            |
|--------------|-------------------------------------------------------|
| Primary Key  | Field(s) that uniquely identify each record in a table |
| Foreign Key  | Field(s) referring to PRIMARY KEY of another table    |
| Super Key    | Set of attributes that can uniquely identify an entity |
| Candidate Key| Minimal superkey with no proper subset                |
| Composite Key| Combination of two or more attributes to identify a row |

## SQL JOINS

| Join Type     | Definition                     | Syntax Example                  |
|--------------|--------------------------------|--------------------------------|
| NATURAL JOIN | Joins tables on columns with same names | `SELECT * FROM employees NATURAL JOIN departments;` |
| SELF JOIN    | Joins a table to itself        | `SELECT e1.name AS employee, e2.name AS manager FROM employees e1 JOIN employees e2 ON e1.manager_id = e2.employee_id;` |
| CROSS JOIN   | Returns Cartesian product      | `SELECT products.name, colors.color_name FROM products CROSS JOIN colors;` |
| INNER JOIN   | Returns only matching rows     | `SELECT orders.order_id, customers.customer_name FROM orders INNER JOIN customers ON orders.customer_id = customers.customer_id;` |
| LEFT JOIN    | All left table rows + matches  | `SELECT employees.name, departments.dept_name FROM employees LEFT JOIN departments ON employees.dept_id = departments.dept_id;` |
| RIGHT JOIN   | All right table rows + matches | `SELECT employees.name, departments.dept_name FROM employees RIGHT JOIN departments ON employees.dept_id = departments.dept_id;` |
| FULL JOIN    | All rows from both tables      | `SELECT employees.name, departments.dept_name FROM employees FULL JOIN departments ON employees.dept_id = departments.dept_id;` |

## COALESCE() vs ISNULL()

| Function      | Behavior                   | Example                     |
|--------------|---------------------------|-----------------------------|
| `COALESCE()` | Returns first non-NULL value | `COALESCE(NULL, 'default')` |
| `ISNULL()`   | Replaces NULL with a value | `ISNULL(column, 0)`         |

## WHERE vs HAVING

| Where                              | Having                                |
|-----------------------------------|---------------------------------------|
| Filters rows before grouping       | Filters groups after aggregation      |
| Used with SELECT, UPDATE, DELETE   | Used with GROUP BY                    |
| Cannot use aggregate functions     | Requires aggregate functions          |
| Executes before GROUP BY           | Executes after GROUP BY               |
| Faster (filters early)             | Slower (filters after grouping)       |

## Clustered vs Non-Clustered Index

| Feature    | Clustered Index            | Non-Clustered Index           |
|------------|----------------------------|-------------------------------|
| Storage    | Physically reorders data   | Separate index structure      |
| Quantity   | One per table              | Multiple per table            |
| Speed      | Faster for retrieval       | Slower (extra lookup)         |

## OLAP vs OLTP

| Feature    | OLAP                       | OLTP                          |
|------------|----------------------------|-------------------------------|
| Purpose    | Analytics (historical data)| Transactions (real-time)      |
| Speed      | Slower                     | Faster                        |
| Example    | Netflix recommendations    | Online ticket booking         |

## NVL vs NVL2

| Function      | Behavior                   | Example                     |
|--------------|---------------------------|-----------------------------|
| `NVL()`      | Returns expr2 if expr1 is NULL | `NVL(NULL, 'backup')`     |
| `NVL2()`     | Returns expr3 if expr1 is NULL | `NVL2(NULL, 'keep', 'replace')` |

## Commit vs Rollback

| Command              | Effect                     | When to use                 |
|----------------------|---------------------------|-----------------------------|
| COMMIT               | Saves changes permanently  | After successful transaction|
| ROLLBACK             | Undoes changes             | On transaction failure      |

## SQL Subsets Commands

| DDL       | CREATE, ALTER, DROP, TRUNCATE, ADD COLUMN, DROP COLUMN |
|----------|-------------------------------------------------------|
| DML      | INSERT, UPDATE, DELETE                                |
| DCL      | GRANT, REVOKE                                         |
| TCL      | COMMIT, ROLLBACK, SAVEPOINT, SET TRANSACTION          |
| DQL      | SELECT                                                |

## Set Operators

| Operator  | Definition                                      | Syntax Example                  |
|----------|------------------------------------------------|--------------------------------|
| UNION    | Combines result sets without duplicates        | `SELECT column1 FROM table1 UNION SELECT column1 FROM table2;` |
| UNION ALL| Combines result sets with duplicates           | `SELECT column1 FROM table1 UNION ALL SELECT column1 FROM table2;` |
| INTERSECT| Returns common records of result sets          | `SELECT column1 FROM table1 INTERSECT SELECT column1 FROM table2;` |
| MINUS    | Returns rows from first SELECT not in second   | `SELECT column1 FROM table1 EXCEPT SELECT column1 FROM table2;` |

## Triggers, Stored Procedures, Views, etc.

### Triggers
Special stored procedures that execute when specified events occur on a table.

**Syntax:**
```sql
CREATE TRIGGER trigger_name
ON table_name
[AFTER | INSTEAD OF] [INSERT | UPDATE | DELETE]
AS
BEGIN
    -- Trigger logic
END;
```

### Stored Procedures
Functions consisting of a group of statements that can be stored and executed when required.

**Syntax:**
```sql
CREATE PROCEDURE sp_name
@param1 datatype,
@param2 datatype
AS
BEGIN
    -- SQL statements
END;

-- Execute
EXEC sp_name;
```

### Views
Virtual tables that display data stored in another table.

**Syntax:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

### Indexes
Special lookup tables used to retrieve data quickly.

**Syntax:**
```sql
CREATE INDEX index_name ON table_name (column_1, column_2);
DROP INDEX index_name;
```

## NULL Values in Aggregate Functions

| Function          | Behavior with NULLs                 | Example                          |
|------------------|-------------------------------------|----------------------------------|
| COUNT(*)         | Counts ALL rows, including NULLs    | `SELECT COUNT(*) FROM employees;` |
| COUNT(column)    | Counts only NON-NULL values         | `SELECT COUNT(manager_id) FROM employees;` |
| SUM()            | Ignores NULL values                 | `SELECT SUM(salary) FROM employees;` |
| AVG()            | Excludes NULL values from calculation | `SELECT AVG(salary) FROM employees;` |
| MIN() and MAX()  | Ignore NULL values                  | `SELECT MIN(commission) FROM sales;` |
| GROUP BY         | NULLs treated as distinct group     | `SELECT department_id, COUNT(*) FROM employees GROUP BY department_id;` |

## Stored Procedure vs Functions

| Features         | Stored Procedure               | Functions                     |
|------------------|--------------------------------|-------------------------------|
| Return Value     | May or may not return values   | Must return a single value    |
| Usage Context    | Executed independently         | Called within SQL statements  |
| DML Operations   | Can perform INSERT, UPDATE, DELETE | Cannot modify database state |
| Transaction Management | Can manage transactions | Cannot manage transactions    |
| Error Handling   | Can use TRY/CATCH blocks       | Limited error handling        |
| Temporary Tables | Can create and use temporary tables | Can only use table variables |

## Window Functions

Window functions apply to aggregate and ranking functions over a particular window (set of rows). The `OVER` clause is used with window functions to define that window.

**Syntax:**
```sql
SELECT column_name1,
window_function(column_name2),
OVER([PARTITION BY column_name1] [ORDER BY column_name3]) AS new_column
FROM table_name;
```

### Window Ranking Functions

| Names        | Role                          | Output Example       | Syntax Example                  |
|--------------|-------------------------------|---------------------|--------------------------------|
| ROW_NUMBER() | Always unique sequential numbers | 1,2,3,4,5,6        | `ROW_NUMBER() OVER(ORDER BY salary DESC)` |
| RANK()       | Same rank for ties, then skips | 1,2,2,4,5,6        | `RANK() OVER(ORDER BY salary DESC)` |
| DENSE_RANK() | Same rank for ties, no skips   | 1,2,2,3,4,5        | `DENSE_RANK() OVER(ORDER BY salary DESC)` |
| LAG()        | Accesses previous row          | Great for comparisons | `LAG(salary, 1) OVER(ORDER BY date)` |
| LEAD()       | Accesses next row              | Useful for looking ahead | `LEAD(salary, 1) OVER(ORDER BY date)` |
| NTILE()      | Divides into buckets           | Good for percentiles | `NTILE(4) OVER(ORDER BY salary DESC)` |

## Avoiding Duplicate Entries Without DISTINCT

DISTINCT can increase query load. Alternatives:

1. **Using ROW_NUMBER():**
```sql
WITH CTE AS (
    SELECT column1, column2,
           ROW_NUMBER() OVER(PARTITION BY column1, column2 ORDER BY column1) AS rn
    FROM your_table
)
SELECT column1, column2 FROM CTE WHERE rn = 1;
```

2. **Using GROUP BY:**
```sql
SELECT column1, column2 FROM your_table GROUP BY column1, column2;
```

3. **Using Self-Join:**
```sql
SELECT t1.column1, t1.column2
FROM your_table t1
WHERE NOT EXISTS (
    SELECT 1 FROM your_table t2
    WHERE t1.column1 = t2.column1
    AND t1.column2 = t2.column2
    AND t1.primary_key > t2.primary_key
);
```

4. **Using UNION:**
```sql
SELECT column1 FROM table1
UNION
SELECT column1 FROM table2;
```

5. **Using MIN/MAX with Self-Join:**
```sql
SELECT t1.column1, t1.column2
FROM your_table t1
JOIN (
    SELECT column1, column2, MIN(primary_key) AS min_id
    FROM your_table
    GROUP BY column1, column2
) t2 ON t1.primary_key = t2.min_id;
```
