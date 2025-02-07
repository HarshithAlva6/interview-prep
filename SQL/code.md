* **SQL:** Structured Query Language to communicate with databases held in RDBMS. (IBM)
Components are Queries, Data Definition Language(CREATE, DROP, ALTER), Data Manipulation Language(INSERT, SELECT, UPDATE, DELETE), Data Control Language(GRANT/REVOKE).
*Forms/RDBMS systems:* Oracle, SQL Server, MySQL, PostgreSQL, SQLite(library)
**Relational Databases:** Use SQL, support ACID(Atomicity, Consistency, Isolation, Durability). Data Integrity through Constraints(Primary and foreign keys). Scalability.
*Benefits* - Structured, ACID Properties, Normalization reduces redundancy and improves integrity; scalability, security.
*Limitations* - Complexity, cost, Fixed schema, cant handle unstructured data, Horizontal scalability.
**SQL vs NoSQL:** Structured with data integrity and complex queries through joins. 
eg: Oracle, SQL Server, MySQL, PostgreSQL, SQLite(library)
NoSQL sacrifices consistency for scalability and performance.Unstructured data in its native form - prone to changes with flexible schema such as image files, maps etc. 
eg: Document(JSON) MongoDB, Key-value(ScyllaDB), Column-family/wide-column stores(Cassandra, HBase), Graph - nodes and edges(GraphQL, Neo4J)
* **SQL Statements:** SELECT, DELETE, INSERT, WHERE, ALTER, NOT NULL
**SQL Keywords:** AS, CREATE, FROM, DROP, UNION, SET, DISTINCT, UPDATE, BETWEEN, ELSE, HAVING, EXISTS, LIMIT, TRUNCATE
**SQL Clause:** JOIN, WHERE, AND, GROUP BY, ORDER BY
* **Data Types:** INTEGER, DECIMAL, CHAR, VARCHAR, DATE, TIMESTAMP, BLOB
* **Operators:** AND, OR, NOT, UNION, INTERSECT, EXCEPT, +, , *, /, IN, LIKE, NOT, OR, SOME

* **DDL:** SQL Subset to define and manage database structure. 
*TRUNCATE* - Helps Drop and create empty table
*ALTER* - Add Column with schema
*CREATE* - Create a table as follows -
CREATE TABLE CUSTOMERS(
   ID          INT NOT NULL,
   NAME        VARCHAR (20) NOT NULL,
   ADDRESS     CHAR (25),
   SALARY      DECIMAL (18, 2),
   PRIMARY KEY (ID)
);
*DROP* - Delete table COMPLETELY.

**DML:** SQL Subset to manage data within the database objects using SQL statements such as SELECT, INSERT, UPDATE, DELETE. 

**JOINS:** 
1. INNER JOIN(Default) - Only Matching pairs from two tables
2. SELF JOIN - Compare values in the same table. Establish the parent-child relationships between different rows in the same table and extract meaningful insights.
3. LEFT JOIN - Keeps all records from left, and missing values from right
4. RIGHT JOIN - Vice verse of above
5. FULL OUTER JOIN - Combines left and right join
6. CROSS JOIN - All possible combinations. Hence no ON property
7. UNION - Vertically combine unique results of same number of columns under SELECT from both tables
8. UNION ALL - Same as above, but considers duplicates too
9. INTERSECT - Matching column values
10. EXCEPT - Columns values that don't match.

* **Clauses:** SELECT, FROM, WHERE, JOIN, GROUP BY, ORDER BY HAVING, INSERT, UPDATE, DELETE - All row updates
**Aggregate Queries:** SUM, COUNT, AVG, MAX, MIN, GROUP BY, HAVING
* **Data/Integrity Constraints:** Rules applied to columns or tables to enforce data integrity and consistency.
*NOT NULL* - Ensures that a column cannot have a NULL value
*UNIQUE* - Ensures that all values in a column are different
*PRIMARY KEY* - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
*FOREIGN KEY* - Prevents actions that would destroy links between tables
*CHECK* - Ensures that the values in a column satisfies a specific condition. eg: AGE int, CHECK(age >=18)
*DEFAULT* - Sets a default value for a column if no value is specified
*CREATE INDEX* - Used to create and retrieve data from the database very quickly

* **SubQueries:** Subqueries, also known as *nested* queries or inner queries, are SQL queries embedded within another query. **Correlated** subquery is a subquery that contains a reference to a table that also appears in the outer query. 
* Types - COLUMN (ALTER TABLE Customers ALTER COLUMN Name FullName), ROW, TABLE, SCALAR (Scalar functions in SQL return a single value based on input parameters)

* **Advanced SQL Functions:** 
1. String Functions - CONCAT, LENGTH, SUBSTRING, REPLACE, UPPER, LOWER (Select, AS)
2. DATE & TIME - DATE(YYYY-MM-DD), DATETIME (YYYY-MM-DD HH:MI:SS), TIMESTAMP(Combines prev values), DATEPART (interval, date), DATEADD(interval, numberToAdd, date), DATEDIFF, FORMAT
3. NUMERIC FUNCTIONS - ROUND, FLOOR, CEILING, ABS, MOD, 
4. CONDITIONAL - CASE(WHEN...THEN...ELSE, END AS ProxyName;), COALESCE(column, newvalue if null), NULLIF (returns NULL if two expressions are equal, otherwise it returns the first expression)

* **Views:** Virtual tables based on the result set of an SQL statement. They act as a saved query that can be treated like a table - Additional security layer that simplify complex queries. 
1. CREATE VIEW view_name AS SELECT ...
2. MODIFY - Modify a VIEW but keeps the VIEW name intact, using ALTER
3. DROP

* **INDEXES:** Separate data structure that allows the database engine for quick lookup mechanism of data without scanning the entire table. While they speed up SELECT queries, indexes can slow down INSERT, UPDATE, and DELETE operations because the index structure must be updated.
* CREATE INDEX index_name ON PERSONS / PERSONS(first, last)
* Database administrators must balance the improved query performance that indexes provide against the overhead they introduce for data modification operations. 

* Indexes defined on key columns/index key. Composite index if more than one key column. Index structure is that of a B-Tree. The index is sorted in the order of the key columns, and the tree structure of the index allows a divide-and-conquer approach to locating rows.
* Some of the basic operations done by SQL over Index -
Scan(All leaf pages), seek(specific value or range), lookup (locate rows affected by a query), updates

* **Optimize SQL Queries:** 
1. Use INDEX effectively
2. Avoid SELECT queries, focus on necessary columns only
3. Reduce use of wildcard characters (LIKE %)
4. Use appropriate Data Types and layouts
5. Avoid redundancy/unnecessary data retrievel (LIMIT)
6. Use EXIST() instead of COUNT() queries (First occurences)
7. Avoid Subqueries, use JOIN
8. Make use of cloud database-specific features for security, integrity, automation, resilience.
9. Query profiling to monitor query performance
10. Utilise rule-based AI
11. Utilise microservice design patterns
12. Adaptive query execution using software designed to process large workloads

* **Transactions:** Transactions in SQL are units of work that group one or more database operations into a single, atomic unit. They ensure data integrity by following the ACID properties: Atomicity (all or nothing), Consistency (database remains in a valid state), Isolation (transactions don’t interfere with each other), and Durability (committed changes are permanent).
* Control Commands - 
BEGIN...END (Start and end a transaction, consiting of operations under a single unit)
COMMIT
ROLLBACK 
SAVEPOINT(Partial commits between Commits - SAVEPOINT savepoint_name; ROLLBACK TO savepoint_name; RELEASE SAVEPOINT SAVEPOINT_NAME;) 
SET TRANSACTION [ READ WRITE | READ ONLY ];

**Transactional Errors overcome by ACID -**
1. Dirty Read: If a transaction is in the middle of updating some data and hasn’t committed yet, and another transaction is allowed to read that uncommitted data, that’s dirty, and could lead to your app showing incorrect data that got rolled back.
2. Non-repeatable Reads: If you’ve got two consecutive reads in one transaction with a concurrent update in between, those reads are going to show different results even though they’re part of the same transaction.
3. Phantom Reads: If a transaction reads data and then a concurrent transaction inserts data that would have been read in the original transaction.

SQL achieve ACID compliance using Locking to hold transactions.
NoSQL DBs are built as distributed systems, governed by CAP theorem — you can’t never have full consistency and full availability; you need to choose one.

**Transaction Isolation Levels:** Degree to which the operations in one transaction are visible to other concurrent transactions. There are typically four standard levels: 
Read Uncommitted (level 0 locking) - Okay if high volumes of read-only data used in analytics
Read Committed (Avoids dirty reads) - Product inventory read, used by default.
Repeatable Read (Avoids anomalies on repeated read)
Serializable - Transactions completely isolated.

**Database Security:** To control access to sensitive data,and hand over same priviledges -
1. GRANT - GRANT UPDATE ON ORDER_BACKLOG TO JONES/PUBLIC WITH GRANT OPTION
2. REVOKE - REVOKE SELECT ON TABLE SMITH.TABLEA FROM BAKER BY ALL
Some of the *best practices* are -
1. Least Priviledge principle
2. Regular Security Updates
3. Complex and Secure Passwords
4. Limit Remote connections
5. Avoid using SQL Server Admin Account
6. Encrypt Information
7. Database Backups
8. Monitoring and Auditing database changes
9. Regular Vulnerability Scanning of security posture
10. SQL Injection reduction using parameterized queries/prepared statements

**Stored Procedures:** Unlike Functiones, they take no parameters, can modify database objects, and need not return results. Functions can be called from procedures, but procedures cannot be called from functions. Procedures cannot be used in SELECT statements, but functions can be embedded in SELECT statements. 

* **Performance Tuning SQL Queries:** To enhance Server performance by reducing resource and time usage. Key strategies include indexing critical columns, optimizing complex query structure, query caching to reduce redundant database calls, reducing the use of resource-intensive operations like JOINs and GROUP BY, selecting only necessary columns (SELECT * should be avoided), and leveraging database-specific features such as partitioning, query hints, and execution plan analysis. Regularly monitoring and analyzing query performance, along with maintaining database health through routine tasks like updating statistics and managing indexes, are also vital to sustaining high performance.
* Query Analysis Techniques -
1. EXPLAIN USING TABULAR/TEXT/JSON SELECT...
- Returns the logical execution plan for the specified SQL statement.
2. Using Indexing
3. Optimize Joins - Use Explicit JOINs, Use EXISTS Instead of IN, Avoid SELECT *, Reduce Join Operations, Use LIMIT and OFFSET Judiciously
4. Reduce subqueries using recursion
5. Selective Projection to choose specific columns
* **Advanced SQL:**
1. Window Functions - Calculations on set of rows(sliding window)
OVER - Designates window function
PARTITION BY - Narrow the window from the entire dataset to individual groups within the dataset
ROW_NUMBER() - Display the number
RANK() - In case of match, same number, but starts next value after skipped row
DENSE_RANK() - would give identical rows a rank of 2, but the following row would be 3—no ranks would be skipped.
LAG(col, #) - gets the difference amount of current to the row number given by # in the past
LEAD(col, #) - gets the difference in future

* **Recursive Queries:** Repeated execution of a query within itself, enabling the traversal of hierarchical or tree-like data structures.
eg: WITH RECURSIVE cte_name (two SELECT statements, each for base case and recursive case)

**Pivot SQL:** Divide components of data into different columns and rows to make it easier to analyze
SELECT [Date] AS 'Day',
    ISNULL([Sammich], 0) AS Sammich,
    ISNULL([Pickle],  0) AS Pickle, 
    ISNULL([Apple],   0) AS Apple,
    ISNULL([Cake],    0) AS Cake
FROM (
    SELECT [Date], FoodName, AmountEaten FROM FoodEaten
) AS SourceTable
PIVOT (
    MAX(AmountEaten)
    FOR FoodName IN (
        [Sammich], [Pickle], [Apple], [Cake]
    )
) AS PivotTable
**Unpivot SQL:**
UNPIVOT monthly_sales
ON jan, feb, mar, apr, may, jun
INTO
    NAME month
    VALUE sales;

**Common Table Expressions:** (CTEs) in SQL are named temporary result sets and defined using WITH clause as virtual tables. Allow for recursive queries.
WITH cte_name (column1, column2, ...) AS (
    SELECT ...
    FROM ...
    WHERE ...
)

* **Dynamic SQL:** Dynamic SQL is a programming method that allows you to build SQL statements dynamically at runtime, in response to input or conditions. Risks include SQL Injection.

sp_executesql is an extended stored procedure that can be used to execute dynamic SQL statements

DECLARE @SQL nvarchar(1000)
declare @Pid varchar(50)
set @pid = '689'
SET @SQL = 'SELECT ProductID,Name,ProductNumber FROM SalesLT.Product where ProductID = '+ @Pid
EXEC (@SQL)