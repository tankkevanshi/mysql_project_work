Last login: Tue Aug 25 07:29:02 on ttys000
kevanshi@Kevanshis-MacBook-Pro ~ % mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 9.7.2 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> CREATE DATABASE ecommerce_store;
Query OK, 1 row affected (0.066 sec)

mysql> USE ecommerce_store;
Database changed
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| collage            |
| collage_db         |
| company_db         |
| ecommerce_store    |
| information_schema |
| inventory_db       |
| lab_work_23        |
| mysql              |
| performance_schema |
| school             |
| school_db          |
| sql_crud           |
| sql_sales          |
| student_db         |
| students           |
| sys                |
+--------------------+
16 rows in set (0.001 sec)

mysql> CREATE TABLE Customers (
    -> CustomerID INT PRIMARY KEY,
    -> Name VARCHAR(10),
    -> Email VARCHAR(100),
    -> Address VARCHAR(200)
    -> );
Query OK, 0 rows affected (0.057 sec)

mysql> DESC Customers;
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| CustomerID | int          | NO   | PRI | NULL    |       |
| Name       | varchar(10)  | YES  |     | NULL    |       |
| Email      | varchar(100) | YES  |     | NULL    |       |
| Address    | varchar(200) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
4 rows in set (0.013 sec)

mysql> INSERT INTO Customers (CustomerID, Name, Email, Address) VALEUS
    -> (1, 'Alice', 'alice@gmail.com', 'Surat'),
    -> (2, 'Bob', 'bob@gmail.com', 'Ahmdabad'),
    -> (3, 'Charlie', 'charlie@gmail.com', 'Vadodra'),
    -> (4, 'David', 'david@gmail.com', 'Mumbai'),
    -> (5, 'Alice', 'alice@gmail.com', 'Rajkot');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'VALEUS
(1, 'Alice', 'alice@gmail.com', 'Surat'),
(2, 'Bob', 'bob@gmail.com', 'Ah' at line 1
mysql> INSERT INTO Customers (CustomerID, Name, Email, Address) VALUES
    -> (1, 'Alice', 'alice@gmail.com', 'Surat'),
    -> (2, 'Bob', 'bob@gmail.com', 'Ahmdabad'),
    -> (3, 'Charlie', 'charlie@gmail.com', 'Vadodra'),
    -> (4, 'David', 'david@gmail.com', 'Mumbai'),
    -> (5, 'Alice', 'alice@gmail.com', 'Rajkot');
Query OK, 5 rows affected (0.008 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM Customers;
+------------+---------+-------------------+----------+
| CustomerID | Name    | Email             | Address  |
+------------+---------+-------------------+----------+
|          1 | Alice   | alice@gmail.com   | Surat    |
|          2 | Bob     | bob@gmail.com     | Ahmdabad |
|          3 | Charlie | charlie@gmail.com | Vadodra  |
|          4 | David   | david@gmail.com   | Mumbai   |
|          5 | Alice   | alice@gmail.com   | Rajkot   |
+------------+---------+-------------------+----------+
5 rows in set (0.001 sec)

mysql> CREATE TABLE Orders (
    -> OrderID INT PRIMARY KEY<
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '<' at line 2
mysql> CREATE TABLE Orders (
    -> OrderID INT PRIMARY KEY,
    -> CustomerID INT,
    -> OrderDate DATE,
    -> TotalAmount DECIMAL(10,2),
    -> FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
    -> );
Query OK, 0 rows affected (0.018 sec)

mysql> DESC Orders;
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| OrderID     | int           | NO   | PRI | NULL    |       |
| CustomerID  | int           | YES  | MUL | NULL    |       |
| OrderDate   | date          | YES  |     | NULL    |       |
| TotalAmount | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
4 rows in set (0.004 sec)

mysql> INSERT INTO Orders (OrderID, CustomerID,OrderDate, TotalAmount) VALUES
    -> (101, 1, '2026-08-01', 1500.00),
    -> (102, 2, '2026-08-05', 2400.00),
    -> (103, 3, '2026-08-10', 1300.00),
    -> (104, 4, '2026-08-15', 3000.00),
    -> (105, 1, '2026-08-20', 1800.00);
Query OK, 5 rows affected (0.005 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM Orders;
+---------+------------+------------+-------------+
| OrderID | CustomerID | OrderDate  | TotalAmount |
+---------+------------+------------+-------------+
|     101 |          1 | 2026-08-01 |     1500.00 |
|     102 |          2 | 2026-08-05 |     2400.00 |
|     103 |          3 | 2026-08-10 |     1300.00 |
|     104 |          4 | 2026-08-15 |     3000.00 |
|     105 |          1 | 2026-08-20 |     1800.00 |
+---------+------------+------------+-------------+
5 rows in set (0.001 sec)

mysql> SELECT * FROM Orders WHERE CustomerID = 1;
+---------+------------+------------+-------------+
| OrderID | CustomerID | OrderDate  | TotalAmount |
+---------+------------+------------+-------------+
|     101 |          1 | 2026-08-01 |     1500.00 |
|     105 |          1 | 2026-08-20 |     1800.00 |
+---------+------------+------------+-------------+
2 rows in set (0.002 sec)

mysql> UPDATE Orders SET TotalAmount = 2800.00 WHERE OrderID = 102;
Query OK, 1 row affected (0.002 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT * FROM Orders;
+---------+------------+------------+-------------+
| OrderID | CustomerID | OrderDate  | TotalAmount |
+---------+------------+------------+-------------+
|     101 |          1 | 2026-08-01 |     1500.00 |
|     102 |          2 | 2026-08-05 |     2800.00 |
|     103 |          3 | 2026-08-10 |     1300.00 |
|     104 |          4 | 2026-08-15 |     3000.00 |
|     105 |          1 | 2026-08-20 |     1800.00 |
+---------+------------+------------+-------------+
5 rows in set (0.001 sec)

mysql> DELETE FROM Orders WHERE OrderID = 105;
Query OK, 1 row affected (0.003 sec)

mysql> SELECT * FROM Orders;
+---------+------------+------------+-------------+
| OrderID | CustomerID | OrderDate  | TotalAmount |
+---------+------------+------------+-------------+
|     101 |          1 | 2026-08-01 |     1500.00 |
|     102 |          2 | 2026-08-05 |     2800.00 |
|     103 |          3 | 2026-08-10 |     1300.00 |
|     104 |          4 | 2026-08-15 |     3000.00 |
+---------+------------+------------+-------------+
4 rows in set (0.000 sec)

mysql> SELECT MAX(TotalAmount) AS Minimum_Amount FROM Orders;
+----------------+
| Minimum_Amount |
+----------------+
|        3000.00 |
+----------------+
1 row in set (0.005 sec)

mysql> SELECT AVG(TotalAmount) AS Average_Amount FROM Orders;
+----------------+
| Average_Amount |
+----------------+
|    2150.000000 |
+----------------+
1 row in set (0.001 sec)

mysql> SELECT Customers.Name, Orders.OrderID, Orders.OrdersDate, Orders.TotalAmount FROM Customers JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
ERROR 1054 (42S22): Unknown column 'Orders.OrdersDate' in 'field list'
mysql> DESC Orders;
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| OrderID     | int           | NO   | PRI | NULL    |       |
| CustomerID  | int           | YES  | MUL | NULL    |       |
| OrderDate   | date          | YES  |     | NULL    |       |
| TotalAmount | decimal(10,2) | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
4 rows in set (0.002 sec)

mysql> SELECT Customers.Name, Orders.OrderID, Orders.OrderDate, Orders.TotalAmount FROM Customers JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
+---------+---------+------------+-------------+
| Name    | OrderID | OrderDate  | TotalAmount |
+---------+---------+------------+-------------+
| Alice   |     101 | 2026-08-01 |     1500.00 |
| Bob     |     102 | 2026-08-05 |     2800.00 |
| Charlie |     103 | 2026-08-10 |     1300.00 |
| David   |     104 | 2026-08-15 |     3000.00 |
+---------+---------+------------+-------------+
4 rows in set (0.001 sec)

mysql> CREATE TABLE Products (
    -> ProductID INT PRIMARY KEY,
    -> ProductName VARCHAR(10),
    -> Price DECIMAL (10,2),
    -> Stock INT
    -> );
Query OK, 0 rows affected (0.012 sec)

mysql> DESC Products;
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| ProductID   | int           | NO   | PRI | NULL    |       |
| ProductName | varchar(10)   | YES  |     | NULL    |       |
| Price       | decimal(10,2) | YES  |     | NULL    |       |
| Stock       | int           | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
4 rows in set (0.002 sec)

mysql> INSERT INTO Products (ProductID, ProductName, Price, Stock) VALUES
    -> (1, 'Laptop', 55000, 10),
    -> (2, 'Keyboard', 1500, 20),
    -> (3, 'Mouse', 800, @),
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 4
mysql> INSERT INTO Products (ProductID, ProductName, Price, Stock) VALUES
    -> (1, 'Laptop', 55000, 10),
    -> (2, 'Keyboard', 1500, 20),
    -> (3, 'Mouse', 800, 2),
    -> (4, 'Moniter', 12000,5),
    -> (5, 'Mobail',30000, 4 ),
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 7
mysql> INSERT INTO Products (ProductID, ProductName, Price, Stock) VALUES
    -> (1, 'Laptop', 55000, 10),
    -> (2, 'Keyboard', 1500, 20),
    -> (3, 'Mouse', 800, 2),
    -> (4, 'Moniter', 12000,5),
    -> (5, 'Mobail',30000, 4 );
Query OK, 5 rows affected (0.003 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM Products;
+-----------+-------------+----------+-------+
| ProductID | ProductName | Price    | Stock |
+-----------+-------------+----------+-------+
|         1 | Laptop      | 55000.00 |    10 |
|         2 | Keyboard    |  1500.00 |    20 |
|         3 | Mouse       |   800.00 |     2 |
|         4 | Moniter     | 12000.00 |     5 |
|         5 | Mobail      | 30000.00 |     4 |
+-----------+-------------+----------+-------+
5 rows in set (0.000 sec)

mysql> SELECT * FROM Products ORDER BY Price DESC;
+-----------+-------------+----------+-------+
| ProductID | ProductName | Price    | Stock |
+-----------+-------------+----------+-------+
|         1 | Laptop      | 55000.00 |    10 |
|         5 | Mobail      | 30000.00 |     4 |
|         4 | Moniter     | 12000.00 |     5 |
|         2 | Keyboard    |  1500.00 |    20 |
|         3 | Mouse       |   800.00 |     2 |
+-----------+-------------+----------+-------+
5 rows in set (0.001 sec)

mysql> UPDATE Products SET Price = 1800 WHERE ProductID = 2;
Query OK, 1 row affected (0.002 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT * FROM Products;
+-----------+-------------+----------+-------+
| ProductID | ProductName | Price    | Stock |
+-----------+-------------+----------+-------+
|         1 | Laptop      | 55000.00 |    10 |
|         2 | Keyboard    |  1800.00 |    20 |
|         3 | Mouse       |   800.00 |     2 |
|         4 | Moniter     | 12000.00 |     5 |
|         5 | Mobail      | 30000.00 |     4 |
+-----------+-------------+----------+-------+
5 rows in set (0.000 sec)

mysql> DELETE FROM Products WHERE Stock = 0;
Query OK, 0 rows affected (0.000 sec)

mysql> SELECT * FROM Products;
+-----------+-------------+----------+-------+
| ProductID | ProductName | Price    | Stock |
+-----------+-------------+----------+-------+
|         1 | Laptop      | 55000.00 |    10 |
|         2 | Keyboard    |  1800.00 |    20 |
|         3 | Mouse       |   800.00 |     2 |
|         4 | Moniter     | 12000.00 |     5 |
|         5 | Mobail      | 30000.00 |     4 |
+-----------+-------------+----------+-------+
5 rows in set (0.000 sec)

mysql> SELECT * FROM Products WHERE Price BETWEEN 500 AND 200;
Empty set (0.000 sec)

mysql> SELECT * FROM Products WHERE Price = (SELECT MAX(Price) FROM Products);
+-----------+-------------+----------+-------+
| ProductID | ProductName | Price    | Stock |
+-----------+-------------+----------+-------+
|         1 | Laptop      | 55000.00 |    10 |
+-----------+-------------+----------+-------+
1 row in set (0.003 sec)

mysql> SELECT * FROM Products WHERE Price = (SELECT MIN(Price) FROM Products;)
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql>  SELECT * FROM Products WHERE Price = (SELECT MIN(Price) FROM Products);
+-----------+-------------+--------+-------+
| ProductID | ProductName | Price  | Stock |
+-----------+-------------+--------+-------+
|         3 | Mouse       | 800.00 |     2 |
+-----------+-------------+--------+-------+
1 row in set (0.001 sec)

mysql> USE Collage;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> CREATE TABLE OrderDeatils(
    -> OrderDetailID INT PRIMARY KEY,
    -> OrderID INT,
    -> ProductID INT,
    -> Quantity INT,
    -> SubTotal DECIMAL(10,2)
    -> );
ERROR 1050 (42S01): Table 'orderdeatils' already exists
mysql> SHOW TABLES;
+-------------------+
| Tables_in_collage |
+-------------------+
| Customer          |
| Customers         |
| OrderDeatils      |
| Orders            |
| products          |
| sales             |
| students          |
+-------------------+
7 rows in set (0.003 sec)

mysql> DESC orderdeatils;
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| OrderDeatilID | int           | NO   | PRI | NULL    |       |
| OrderID       | int           | YES  |     | NULL    |       |
| ProductID     | int           | YES  |     | NULL    |       |
| Quantity      | int           | YES  |     | NULL    |       |
| SubTotal      | decimal(10,2) | YES  |     | NULL    |       |
+---------------+---------------+------+-----+---------+-------+
5 rows in set (0.002 sec)

mysql> INSERT INTO orderdeatils(OrderDeatilID, OrderID, ProductID, Quantity, SubTotal)VALUES
    -> (1, 101, 1, 2, 110000),
    -> (2, 102, 2, 3, 4500),
    -> (3, 103, 3, 5, 4000),
    -> (4, 103, 4, 2, 24000),
    -> ;)
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 5
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql>  INSERT INTO orderdeatils(OrderDeatilID, OrderID, ProductID, Quantity, SubTotal)VALUES
    -> (1, 101, 1, 2, 110000),
    -> (2, 102, 2, 3, 4500),
    -> (3, 103, 3, 5, 4000),
    -> (4, 104, 4, 2, 24000),
    -> (5, 101, 5, 4, 8000);
Query OK, 5 rows affected (0.004 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM orderdeatils;
+---------------+---------+-----------+----------+-----------+
| OrderDeatilID | OrderID | ProductID | Quantity | SubTotal  |
+---------------+---------+-----------+----------+-----------+
|             1 |     101 |         1 |        2 | 110000.00 |
|             2 |     102 |         2 |        3 |   4500.00 |
|             3 |     103 |         3 |        5 |   4000.00 |
|             4 |     104 |         4 |        2 |  24000.00 |
|             5 |     101 |         5 |        4 |   8000.00 |
+---------------+---------+-----------+----------+-----------+
5 rows in set (0.001 sec)

mysql> SHOW TABLES;
+-------------------+
| Tables_in_collage |
+-------------------+
| Customer          |
| Customers         |
| OrderDeatils      |
| Orders            |
| products          |
| sales             |
| students          |
+-------------------+
7 rows in set (0.001 sec)

mysql> DESC orderdeatils;
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| OrderDeatilID | int           | NO   | PRI | NULL    |       |
| OrderID       | int           | YES  |     | NULL    |       |
| ProductID     | int           | YES  |     | NULL    |       |
| Quantity      | int           | YES  |     | NULL    |       |
| SubTotal      | decimal(10,2) | YES  |     | NULL    |       |
+---------------+---------------+------+-----+---------+-------+
5 rows in set (0.002 sec)

mysql> SELECT * FROM orderdeatils WHERE OrderID = 101;
+---------------+---------+-----------+----------+-----------+
| OrderDeatilID | OrderID | ProductID | Quantity | SubTotal  |
+---------------+---------+-----------+----------+-----------+
|             1 |     101 |         1 |        2 | 110000.00 |
|             5 |     101 |         5 |        4 |   8000.00 |
+---------------+---------+-----------+----------+-----------+
2 rows in set (0.001 sec)

mysql> SELECT SUM(SubTotal) AS TotalRevenue FROM orderdeatils;
+--------------+
| TotalRevenue |
+--------------+
|    150500.00 |
+--------------+
1 row in set (0.002 sec)

mysql> SELECT ProductID, SUM(Quantity) AS TotalQuantity FROME orderdeatils GROUP BY ProductID ORDER BY TotalQuantity DESC LIMIT #;
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROME orderdeatils GROUP BY ProductID ORDER BY TotalQuantity DESC LIMIT #' at line 1
mysql> SELECT ProductID, SUM(Quantity) AS TotalQuantity FROME orderdeatils GROUP BY ProductID ORDER BY TotalQuantity DESC LIMIT 3;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROME orderdeatils GROUP BY ProductID ORDER BY TotalQuantity DESC LIMIT 3' at line 1
mysql> SELECT ProductID, SUM(Quantity) AS TotalQuantity FROM orderdeatils GROUP BY TotalQuantity DESC LIMIT 3;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'DESC LIMIT 3' at line 1
mysql> SELECT ProductID, SUM(Quantity) AS TotalQuantity FROM orderdeatils GROUP BY ProductID ORDER BY TotalQuantity DESC
    -> ;
+-----------+---------------+
| ProductID | TotalQuantity |
+-----------+---------------+
|         3 |             5 |
|         5 |             4 |
|         2 |             3 |
|         1 |             2 |
|         4 |             2 |
+-----------+---------------+
5 rows in set (0.006 sec)

mysql> SELECT ProductID, SUM(Quantity) AS TotalQuantity FROM orderdeatils GROUP BY ProductID ORDER BY TotalQuantity DESC LIMIT 3;
+-----------+---------------+
| ProductID | TotalQuantity |
+-----------+---------------+
|         3 |             5 |
|         5 |             4 |
|         2 |             3 |
+-----------+---------------+
3 rows in set (0.001 sec)

mysql> SELECT COUNT(*) AS TimesSold FROM orderdeatils WHERE ProductID = 2;
+-----------+
| TimesSold |
+-----------+
|         1 |
+-----------+
1 row in set (0.001 sec)

mysql> 
