Last login: Sat Sep 26 15:44:25 on console
kevanshi@Kevanshis-MacBook-Pro ~ % mysql-u root -p
zsh: command not found: mysql-u
kevanshi@Kevanshis-MacBook-Pro ~ % mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 9.7.2 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> CREATE data_transfer;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'data_transfer' at line 1
mysql> CREATE DATABASE data_transfer;
Query OK, 1 row affected (0.017 sec)

mysql> USE data_transfer;
Database changed
mysql> CREATE TABLE Customers(
    -> CustomerID INT PRIMARY KEY,
    -> FirstName VARCHAR(50),
    -> LastName VARCHAR(50),
    -> Email VARCHAR(100),
    -> RegitrastionDate DATE
    -> );
Query OK, 0 rows affected (0.022 sec)

mysql> DESC Customers;
+------------------+--------------+------+-----+---------+-------+
| Field            | Type         | Null | Key | Default | Extra |
+------------------+--------------+------+-----+---------+-------+
| CustomerID       | int          | NO   | PRI | NULL    |       |
| FirstName        | varchar(50)  | YES  |     | NULL    |       |
| LastName         | varchar(50)  | YES  |     | NULL    |       |
| Email            | varchar(100) | YES  |     | NULL    |       |
| RegitrastionDate | date         | YES  |     | NULL    |       |
+------------------+--------------+------+-----+---------+-------+
5 rows in set (0.014 sec)

mysql> INSERT INTO Customers (CustomerID, FirstName, LastName, Email, RegitrastionDate) VALUES(1, 'Ankit', 'Doe', 'ankit123@email.com', '2026-01-11'),
    -> ..;;;;;....//'';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '..' at line 2
ERROR: 
No query specified

ERROR: 
No query specified

ERROR: 
No query specified

ERROR: 
No query specified

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '....//''' at line 1
mysql> INSERT INTO Customers (CustomerID, FirstName, LastName, Email, RegitrastionDate) VALUES 
    -> (1, 'Ankit', 'Doe', 'ankit123@email.com', '2026-01-11'),
    -> (2, 'Subham', 'Smith', 'subham222@email.com', '2025-02-10');
Query OK, 2 rows affected (0.023 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM Customers;
+------------+-----------+----------+---------------------+------------------+
| CustomerID | FirstName | LastName | Email               | RegitrastionDate |
+------------+-----------+----------+---------------------+------------------+
|          1 | Ankit     | Doe      | ankit123@email.com  | 2026-01-11       |
|          2 | Subham    | Smith    | subham222@email.com | 2025-02-10       |
+------------+-----------+----------+---------------------+------------------+
2 rows in set (0.002 sec)

mysql> CREATE TABLE Orders(
    -> OrderID INT PRIMARY KEY,
    -> CustomerID INT,
    -> OrderDate DATE,
    -> TotalAmount DECIMAL(10,2)
    -> );
Query OK, 0 rows affected (0.011 sec)

mysql> DESC Orders;
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| OrderID     | int           | NO   | PRI | NULL    |       |
| CustomerID  | int           | YES  |     | NULL    |       |
| OrderDate   | date          | YES  |     | NULL    |       |
| TotalAmount | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
4 rows in set (0.002 sec)

mysql> INSERT INTO Orders (OrderID, CustomerID, OrderDate, TotalAmount) VALUES
    -> (101, 1, '2026-02-02', 170.20),
    -> (102, 2, '2026-02-04', 200.45);
Query OK, 2 rows affected (0.003 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM Orders;
+---------+------------+------------+-------------+
| OrderID | CustomerID | OrderDate  | TotalAmount |
+---------+------------+------------+-------------+
|     101 |          1 | 2026-02-02 |      170.20 |
|     102 |          2 | 2026-02-04 |      200.45 |
+---------+------------+------------+-------------+
2 rows in set (0.001 sec)

mysql> CREATE TABLE Employees (
    -> EmployeeID INT PRIMARY KEY,
    -> EmployeeName VARCHAR(50),
    -> ^c
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '^c' at line 4
mysql> CREATE TABLE Employees (
    -> EmployeeID INT PRIMARY KEY,
    -> FirstName VARCHAR(50),
    -> LastName VARCHAR(50),
    -> Department VARCHAR(50),
    -> HireDate DATE,
    -> Salary DECIMAL (10,2)
    -> );
Query OK, 0 rows affected (0.011 sec)

mysql> DESC Employees;
+------------+---------------+------+-----+---------+-------+
| Field      | Type          | Null | Key | Default | Extra |
+------------+---------------+------+-----+---------+-------+
| EmployeeID | int           | NO   | PRI | NULL    |       |
| FirstName  | varchar(50)   | YES  |     | NULL    |       |
| LastName   | varchar(50)   | YES  |     | NULL    |       |
| Department | varchar(50)   | YES  |     | NULL    |       |
| HireDate   | date          | YES  |     | NULL    |       |
| Salary     | decimal(10,2) | YES  |     | NULL    |       |
+------------+---------------+------+-----+---------+-------+
6 rows in set (0.003 sec)

mysql> INSERT INTO Employees (EmployeeId, FirstName, LastName, Department, Hiredate, Salary)VALUES
    -> (1, 'Amit', 'Shah', 'Sales', '2026-01-15', 50000),
    -> (2, 'Priya', 'Maheta', 'HR', '2026-04-12', 65000);
Query OK, 2 rows affected (0.004 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM Employees;
+------------+-----------+----------+------------+------------+----------+
| EmployeeID | FirstName | LastName | Department | HireDate   | Salary   |
+------------+-----------+----------+------------+------------+----------+
|          1 | Amit      | Shah     | Sales      | 2026-01-15 | 50000.00 |
|          2 | Priya     | Maheta   | HR         | 2026-04-12 | 65000.00 |
+------------+-----------+----------+------------+------------+----------+
2 rows in set (0.001 sec)

mysql> SELECT
    -> O.OrderID,
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> C.Email,
    -> O.OrderDate,
    -> O.TotalAmount
    -> FROM Orders O
    -> INNER JOIN Customers C ON O.CustomerID = C.CustomerID;
+---------+------------+-----------+----------+---------------------+------------+-------------+
| OrderID | CustomerID | FirstName | LastName | Email               | OrderDate  | TotalAmount |
+---------+------------+-----------+----------+---------------------+------------+-------------+
|     101 |          1 | Ankit     | Doe      | ankit123@email.com  | 2026-02-02 |      170.20 |
|     102 |          2 | Subham    | Smith    | subham222@email.com | 2026-02-04 |      200.45 |
+---------+------------+-----------+----------+---------------------+------------+-------------+
2 rows in set (0.001 sec)

mysql> SELECT
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderID,
    -> O.orderDate,
    -> O.TotalAmount
    -> FROM Customers LEFT JOIN Orders 
    -> ON Customers.CustomerID = Orders.CustomerID;
ERROR 1054 (42S22): Unknown column 'C.CustomerID' in 'field list'
mysql> SELECT
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderID,
    -> O.OrderDate,
    -> O.TotalAmount
    -> FROM Customers LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
ERROR 1054 (42S22): Unknown column 'C.CustomerID' in 'field list'
mysql>  SELECT
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderID,
    -> O.orderDate,
    -> O.TotalAmount
    -> FROM Customers C LEFT JOIN Orders O ON C.CustomerID = O.CustomerID;
+------------+-----------+----------+---------+------------+-------------+
| CustomerID | FirstName | LastName | OrderID | orderDate  | TotalAmount |
+------------+-----------+----------+---------+------------+-------------+
|          1 | Ankit     | Doe      |     101 | 2026-02-02 |      170.20 |
|          2 | Subham    | Smith    |     102 | 2026-02-04 |      200.45 |
+------------+-----------+----------+---------+------------+-------------+
2 rows in set (0.001 sec)

mysql> SELECT 
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderID,
    -> O.OrderDate,
    -> O.TotalAmount
    -> FROM Orders LEFT JOIN C ON O.CustomerID = C.CustomerID;
ERROR 1146 (42S02): Table 'data_transfer.c' doesn't exist
mysql> SELECT
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderID,
    -> O.OrderDate,
    -> O.TotalAmount
    -> FROM Orders O  LEFT JOIN C ON O.CustomerID = C.CustomerID;
ERROR 1146 (42S02): Table 'data_transfer.c' doesn't exist
mysql> SELECT 
    ->     -> C.CustomerID,
    ->     -> C.FirstName,
    ->     -> C.LastName,
    ->     -> O.OrderID,
    ->     -> O.OrderDate,
    ->     -> O.TotalAmount
    ->     -> FROM Orders LEFT JOIN C ON O.CustomerID = C.CustomerID;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '-> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderID,
    ->' at line 2
mysql> ERROR 1146 (42S02): Table 'data_transfer.c' doesn't exist
    '> mysql> 
    '> ';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ERROR 1146 (42S02): Table 'data_transfer.c' doesn't exist
mysql> 
'' at line 1
mysql> SELECT 
    ->     -> C.CustomerID,
    ->     -> C.FirstName,
    ->     -> C.LastName,
    ->     -> O.OrderID,
    ->     -> O.OrderDate,
    ->     -> O.TotalAmount
    ->     -> FROM Orders LEFT JOIN C ON O.CustomerID = C.CustomerID;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '-> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderID,
    ->' at line 2
mysql> ERROR 1146 (42S02): Table 'data_transfer.c' doesn't exist
    '> mysql> 
    '> ;
    '> ';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ERROR 1146 (42S02): Table 'data_transfer.c' doesn't exist
mysql> 
;
'' at line 1
mysql> SELECT 
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderID,
    -> O.OrderDate,
    -> O.TotalAmount
    -> FROM Orders O
    -> LEFT JOIN Customers C ON O.CustomerID = C.CustomerID;
+------------+-----------+----------+---------+------------+-------------+
| CustomerID | FirstName | LastName | OrderID | OrderDate  | TotalAmount |
+------------+-----------+----------+---------+------------+-------------+
|          1 | Ankit     | Doe      |     101 | 2026-02-02 |      170.20 |
|          2 | Subham    | Smith    |     102 | 2026-02-04 |      200.45 |
+------------+-----------+----------+---------+------------+-------------+
2 rows in set (0.001 sec)

mysql> SELECT 
    -> O.OrderID,
    -> O.OrderDate,
    -> O.TotalAmount,
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName FROM Customers
    -> RIGHT JOIN Orders
    -> ON C.CustomerID = O.CustomerID;
ERROR 1054 (42S22): Unknown column 'O.OrderID' in 'field list'
mysql> SELECT 
    -> C.customerID,
    -> C.FirstName,
    -> C.LastName,
    -> O.OrderDate,
    -> O.TotalAmount
    -> FROM Customers C 
    -> RIGHT JOIN Orders O ON C.customerID = O.CustomerID;
+------------+-----------+----------+------------+-------------+
| customerID | FirstName | LastName | OrderDate  | TotalAmount |
+------------+-----------+----------+------------+-------------+
|          1 | Ankit     | Doe      | 2026-02-02 |      170.20 |
|          2 | Subham    | Smith    | 2026-02-04 |      200.45 |
+------------+-----------+----------+------------+-------------+
2 rows in set (0.001 sec)

  [Bookmarked 26 Sep 2026 at 11:46:38 PM]
mysql> SELECT * FROM Customers FULL OUTER JOIN Orders 
    -> ON C.CustomerID = O.CustomerID;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'OUTER JOIN Orders 
ON C.CustomerID = O.CustomerID' at line 1
mysql> SELECT * FROM Customer C
    -> LEFT JOIN Orders O
    -> ON C.CustomerID = O.CustomerID
    -> UNION
    -> SELECT * FROM Customers C
    -> RIGHT JOIN Orders O
    -> ON C.CustomerID = O.CustomerID;
ERROR 1146 (42S02): Table 'data_transfer.customer' doesn't exist
mysql> SELECT * FROM Customers C
    -> LEFT JOIN Orders O
    -> |
    -> ...;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '|
...' at line 3
mysql> SELECT * FROM Customers C
    -> LEFT JOIN Orders O
    -> ON C.Customers O
    -> ,,;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'O
,,' at line 3
mysql> SELECT *
    -> FROM Customers C
    -> LEFT JOIN Orders O
    -> ON C.CustomerID = O.CustomerID
    -> UNION
    -> SELECT * FROM Customers C
    -> RIGHT JOIN Orders O
    -> ON C.CustomerID = O.CustomerID;
+------------+-----------+----------+---------------------+------------------+---------+------------+------------+-------------+
| CustomerID | FirstName | LastName | Email               | RegitrastionDate | OrderID | CustomerID | OrderDate  | TotalAmount |
+------------+-----------+----------+---------------------+------------------+---------+------------+------------+-------------+
|          1 | Ankit     | Doe      | ankit123@email.com  | 2026-01-11       |     101 |          1 | 2026-02-02 |      170.20 |
|          2 | Subham    | Smith    | subham222@email.com | 2025-02-10       |     102 |          2 | 2026-02-04 |      200.45 |
+------------+-----------+----------+---------------------+------------------+---------+------------+------------+-------------+
2 rows in set (0.045 sec)

mysql> SELECT DISTINCT 
    -> C.CustomerID,
    -> C.FirstName,
    -> C.LastName FROM Customer C
    -> JOIN Orders O ON C.CustomerID =O.CustomerID
    -> WHERE O.TotalAmount > (SELECT AVG (TotalAmount) FROM Orders);
ERROR 1146 (42S02): Table 'data_transfer.customer' doesn't exist
mysql> SELECT DISTINCT
    -> C.CustomerID,
    -> C.firstName,
    -> C.LastName
    -> FROM Customers C
    -> JOIN Orders O
    -> ON C.CustomerID = O.CustomerID
    -> WHERE O.TotalAmount > (
    -> SELECT AVG(TotalAmount)
    -> FROM Orders 
    -> );
+------------+-----------+----------+
| CustomerID | firstName | LastName |
+------------+-----------+----------+
|          2 | Subham    | Smith    |
+------------+-----------+----------+
1 row in set (0.007 sec)

mysql> SHOW TABLES;
+-------------------------+
| Tables_in_data_transfer |
+-------------------------+
| Customers               |
| Employees               |
| Orders                  |
+-------------------------+
3 rows in set (0.025 sec)

mysql> SELECT * FROM EMployees
    -> WHERE Salary > (SELECT AVG(Salary) FROM Employees);
+------------+-----------+----------+------------+------------+----------+
| EmployeeID | FirstName | LastName | Department | HireDate   | Salary   |
+------------+-----------+----------+------------+------------+----------+
|          2 | Priya     | Maheta   | HR         | 2026-04-12 | 65000.00 |
+------------+-----------+----------+------------+------------+----------+
1 row in set (0.002 sec)

mysql> SELECT YEAR (OrderDate) AS Year, MONTH(OrderDate) AS Month FROM Orders;
+------+-------+
| Year | Month |
+------+-------+
| 2026 |     2 |
| 2026 |     2 |
+------+-------+
2 rows in set (0.002 sec)

mysql> SELECT OrderDate, DATEDIFF(CURDATE(), OrderDate) AS DaysDifference FROM Orders;
+------------+----------------+
| OrderDate  | DaysDifference |
+------------+----------------+
| 2026-02-02 |            237 |
| 2026-02-04 |            235 |
+------------+----------------+
2 rows in set (0.002 sec)

mysql> SELECT DATE_FORMAT(OrderDate, '%d-%b-%Y')AS FormatteDate FROM Orders;
+--------------+
| FormatteDate |
+--------------+
| 02-Feb-2026  |
| 04-Feb-2026  |
+--------------+
2 rows in set (0.001 sec)

mysql> SELECT CONCAT (FirstName, '', LastName) AS FullName FROM Customers;
+-------------+
| FullName    |
+-------------+
| AnkitDoe    |
| SubhamSmith |
+-------------+
2 rows in set (0.002 sec)

mysql> SELECT REPLACE(FirstName, 'Ankit', 'John') AS FirstName
    -> FROM Customers;
+-----------+
| FirstName |
+-----------+
| John      |
| Subham    |
+-----------+
2 rows in set (0.001 sec)

mysql>  SELECT UPPER(FirstName) AS FirstName,
    -> LOWER(LastName) AS LastName
    -> FROM Customers;
+-----------+----------+
| FirstName | LastName |
+-----------+----------+
| ANKIT     | doe      |
| SUBHAM    | smith    |
+-----------+----------+
2 rows in set (0.001 sec)

mysql> SELECT TRIM(Email) AS CleanEmail FROM Cuatomers;
ERROR 1146 (42S02): Table 'data_transfer.cuatomers' doesn't exist
mysql> SELECT TRIM(Email) AS CleanEmail FROM cuatomers;
ERROR 1146 (42S02): Table 'data_transfer.cuatomers' doesn't exist
mysql> SELECT TRIM(Email) AS CleanEmail FROM Customers;
+---------------------+
| CleanEmail          |
+---------------------+
| ankit123@email.com  |
| subham222@email.com |
+---------------------+
2 rows in set (0.001 sec)

mysql> SELECT 
    -> OrderID,
    -> TotalAmount,
    -> SUM(TotalAmount) OVER (ORDER BY OrderID) AS RunningTotal
    -> FROM Orders;
+---------+-------------+--------------+
| OrderID | TotalAmount | RunningTotal |
+---------+-------------+--------------+
|     101 |      170.20 |       170.20 |
|     102 |      200.45 |       370.65 |
+---------+-------------+--------------+
2 rows in set (0.003 sec)

mysql> SELECT
    -> OrderID,
    -> TotalAmount,
    -> RANK () OVER (ORDER BY TotalAmount DESC) AS OrderRank
    -> FROM Orders;
+---------+-------------+-----------+
| OrderID | TotalAmount | OrderRank |
+---------+-------------+-----------+
|     102 |      200.45 |         1 |
|     101 |      170.20 |         2 |
+---------+-------------+-----------+
2 rows in set (0.002 sec)

mysql> SELECT
    -> OrderID,
    -> TotalAmount,
    -> CASE
    -> WHEN TotalAmount > 1000 THEN '10% Off'
    -> WHEN TotalAmount > 500 THEN '5% Off'
    -> ELSE 'No Discount'
    -> END AS Discount
    -> FROM Orders;
+---------+-------------+-------------+
| OrderID | TotalAmount | Discount    |
+---------+-------------+-------------+
|     101 |      170.20 | No Discount |
|     102 |      200.45 | No Discount |
+---------+-------------+-------------+
2 rows in set (0.001 sec)

mysql> SELECT
    -> EmployeeID,
    -> FirstName,
    -> Salary,
    -> CASE
    -> WHEN Salary > 70000 THEN 'High'
    -> WHEN Salary > 40000 THEN 'Medium'
    -> ELSE AS SalaryCategory
    -> FROM Employees;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'AS SalaryCategory
FROM Employees' at line 8
mysql> SELECT
    -> EmployeeID,
    -> FirstName,
    -> Salary,
    -> CASE
    -> WHEN Salary > 70000 THEN 'High'
    -> WHEN Salary > 40000 THEN 'Medium'
    -> ELSE 'Low'
    -> END AS SalaryCategory
    -> FROM Employees;
+------------+-----------+----------+----------------+
| EmployeeID | FirstName | Salary   | SalaryCategory |
+------------+-----------+----------+----------------+
|          1 | Amit      | 50000.00 | Medium         |
|          2 | Priya     | 65000.00 | Medium         |
+------------+-----------+----------+----------------+
2 rows in set (0.001 sec)

mysql> 
