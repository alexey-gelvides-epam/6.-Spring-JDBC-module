# 6. Spring JDBC module. JDBC Advanced Techniques (+ Spring JDBC)

## Topics: 

- JDBC queries, parameters, exceptions
- Connection polling, transactions, batches, and properties of driver 
- Mapping results, logging
- Spring with JDBC

## Task 1

1 point.

1. Create simple database with tables:
    - Users (id, name, surname, birthdate);
    - Friendships (userid1, userid2, timestamp);
    - Posts (id, userId, text, timestamp);
    - Likes (postid, userid, timestamp).
2. Populate tables with data which are make sense (> 1 000 users, > 70 000 friendships, > 300 000 likes in 2025). *
3. Program should print out all names (only distinct) of users who has more than 100 friends and 100 likes in March 2025. Implement all actions (table creation, insert data and reading) with SpringJDBC.

## Task 2

1 point.

Create a Highload Writing Console Tool that populates the database (URL/Name are configuration settings).

Required functionality:
- It creates N random tables with random unique name (or names from dictionary) and K random columns with type taken from Z random types.
- It creates m random rows for the i-th table, where m is an i-th element of M. M is an N-dimensional array predefined by a user of this tool.
- It supports the table creation/populating via L concurrent connections (from different threads or from a few instances of classes running simultaneously).
- All settings are located in a configuration file; the path to this file is a parameter of main() function.

Discuss with mentor how to improve performance of the suggested solution. 

## Task 3

1 point.

Create a Database Copy Console Tool that copies the database (URL/Name are command line parameters) step-by-step (table by table).

Required functionality:
- Copying of tables in lexicographic order.
- Rows in direct or reverse order (command line parameter).
- It works for 10 GB database in minimal time (should tune performance using Java and database performance features).
- The solution is delivered with a test database (populated with a huge volume of data).

**10 GB sample database could be generated via Highload Writing Tool.**

## Task 4 

1 point.

Add five DBUnit tests to appropriate project (pet project) or another. Prepare test datasets if it is required.

## Task 5

1 point.

- Take the existing (or write from zero) JDBC solution with a few CRUD operations and more complex SQL (for simple report generation) and migrate it to stored procedures. *
- Write SQL script to create those stored procedures with Java style parameters and specific external names. **
- Write a test which drops all stored procedures and creates a few of them via Java code.
- Also, provide the script to print out all stored procedure in your database and dropping them for test purposes, for example.
- Check that the application works properly, all test are green and so on.
- Compare the performance of two solutions; explain to your mentor the benefits or disadvantages of storage procedure usage for the taken application.

** 3-5 tables with CRUD operations and two complex SELECTs can be enough. **
** Use MySQL or PostgreSQL or Oracle. **

## Task 6 

2 points.

If your database * has pre-defined storage procedure, use a few of them to print out interesting information or maintain something in the database.

** Use MySQL or PostgreSQL or Oracle. **

## Task 7

1 point.

Implement the next use cases of File Share application:

1. Save file to the database.
2. Retrieve file from the database.
3. Optional: file expiration.

Large files should be supported (size up to 200 MB).

Acceptance criteria:
- File Share database schema is developed:
    - DB schema diagram is provided (5 points);
    - stored procedures for saving and retrieving files from DB are created (5 points).
- DAO on JDBC is implemented:
    - DAO methods that are not used in proposed use cases can throw UnsupportedOperationException (2 points);
    - CallableStatement is used to call DB stored procedures (3 points);
    - large binary files are retrievable from DB (5 points).

Think about pros and cons of stored procedures usage comparing to SQL statement stored in Java code. Describe what difficulties you’ve faced when working with large binary files. Make demo via console interface or via special main method.

## Task 8

1 point.

Write your own annotation-based or XML-based JabaORM that parses specific class and generates SQL-queries for CRUD (or SCRUD) operations.

Your mini-ORM should have one entry point, which supports CRUD operations for parsed class passed as a parameter in methods.

- .save
- .load
- .update
- .delete

Implement all actions via RowSet if it is possible.

## Lectures

- JDBC Intro - https://learn.epam.com/detailsPage?id=5806341b-5753-4dd9-b9ba-40275580fd0f
- Spring JDBC - https://spring.io/guides/gs/relational-data-access/

## Documentations

- JDBC Tutorial from Oracle - https://docs.oracle.com/javase/tutorial/jdbc/basics/index.html
- JDBC from A to Z - https://www.tutorialspoint.com/jdbc/index.htm
- JDBC Result set - https://www.tutorialspoint.com/jdbc/jdbc-result-sets.htm
- JDBC batching - https://www.tutorialspoint.com/jdbc/jdbc-batch-processing.htm
- JDBC data streaming - https://www.tutorialspoint.com/jdbc/jdbc-streaming-data.htm

## Sites

- Connections - https://www.tutorialspoint.com/jdbc/jdbc-db-connections.htm
- JDBC Basics - https://blog.jooq.org/2015/09/24/it-is-all-about-the-jdbc-basics/
- Stored Procedures in Java - https://docs.oracle.com/cd/B19306_01/java.102/b14187/chfive.htm
- How to work with Stored Procedures (from Oracle) - https://docs.oracle.com/javase/tutorial/jdbc/basics/storedprocedures.html
- Connection Pooling + connection/resource leaks: 
    - https://vladmihalcea.com/2014/04/17/the-anatomy-of-connection-pooling/
    - https://vladmihalcea.com/2016/07/12/the-best-way-to-detect-database-connection-leaks/
    - https://blog.jooq.org/2017/01/05/how-to-prevent-jdbc-resource-leaks-with-jdbc-and-with-jooq/
- JDBC Statements logging
    - https://vladmihalcea.com/2016/05/03/the-best-way-to-log-jdbc-statements/
- JDBC Batch Updates (+performance)
    - http://tutorials.jenkov.com/jdbc/batchupdate.html
    - https://vladmihalcea.com/2017/03/21/how-to-find-which-statement-failed-in-a-jdbc-batch-update/
    - https://blog.jooq.org/2017/02/06/how-to-execute-sql-batches-with-jdbc-and-jooq/
- JDBC Streaming + Batch processing (+reactive statistics)"
    - https://vladmihalcea.com/2016/11/23/how-does-mysql-result-set-streaming-perform-vs-fetching-the-whole-jdbc-resultset-at-once/
    - https://www.jooq.org/java-8-and-sql
    - https://www.jooq.org/doc/3.9/manual/sql-execution/fetching/lazy-fetching/
    - http://use-the-index-luke.com/sql/partial-results/fetch-next-page
    - http://www.nurkiewicz.com/2015/07/server-sent-events-with-rxjava-and.html
