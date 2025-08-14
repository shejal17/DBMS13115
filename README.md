Microsoft Windows [Version 10.0.22631.4602]
(c) Microsoft Corporation. All rights reserved.

C:\Program Files\MySQL\MySQL Server 9.3\bin>mysql -h localhost -u root -p
Enter password: ****
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 67
Server version: 9.3.0 MySQL Community Server - GPL

Copyright (c) 2000, 2025, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database inventory;
Query OK, 1 row affected (0.272 sec)

mysql> use inventory;
Database changed
mysql> create table product(pid int primary key, pname varchar(20),price float);
Query OK, 0 rows affected (0.524 sec)

mysql> create table sale(sid int,pid int,qty int,FOEREIGN KEY(pid)REFERENCES product(pid));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'KEY(pid)REFERENCES product(pid))' at line 1
mysql> create table sale(sid int,pid int,qty int,FOREIGN KEY(pid)REFERENCES product(pid));
Query OK, 0 rows affected (0.783 sec)

mysql> create table supplier(suppid int,sname varchar(30),address varchar(30));
Query OK, 0 rows affected (0.440 sec)

mysql> alter table supplier add primary key(suppid),add CONSTRAINT chk CHECK(suppid>900);
Query OK, 0 rows affected (0.719 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc product;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| pid   | int         | NO   | PRI | NULL    |       |
| pname | varchar(20) | YES  |     | NULL    |       |
| price | float       | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.325 sec)

mysql> desc sale;
+-------+------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+-------+------+------+-----+---------+-------+
| sid   | int  | YES  |     | NULL    |       |
| pid   | int  | YES  | MUL | NULL    |       |
| qty   | int  | YES  |     | NULL    |       |
+-------+------+------+-----+---------+-------+
3 rows in set (0.035 sec)

mysql> desc supplier;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| suppid  | int         | NO   | PRI | NULL    |       |
| sname   | varchar(30) | YES  |     | NULL    |       |
| address | varchar(30) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
3 rows in set (0.024 sec)

mysql> CREATE USER 'rajesh'@'localhost' IDENTIFIED BY 'r1234';
Query OK, 0 rows affected (0.241 sec)

mysql> grant select on inventory.*TO'rajesh'@localhost;
Query OK, 0 rows affected (0.234 sec)

mysql> CREATE USER 'mohit'@'localhost' IDENTIFIED BY 'm1234';
Query OK, 0 rows affected (0.224 sec)

mysql> grant all privileges on inventory.*TO'mohit'@localhost;
Query OK, 0 rows affected (0.191 sec)

USER MOHIT:
Microsoft Windows [Version 10.0.22631.4602]
(c) Microsoft Corporation. All rights reserved.

C:\Program Files\MySQL\MySQL Server 9.3\bin>mysql -h localhost -u mohit -p
Enter password: *****
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 69
Server version: 9.3.0 MySQL Community Server - GPL

Copyright (c) 2000, 2025, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use inventory;
Database changed
mysql> desc product;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| pid   | int         | NO   | PRI | NULL    |       |
| pname | varchar(20) | YES  |     | NULL    |       |
| price | float       | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.214 sec)

mysql> desc supplier;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| suppid  | int         | NO   | PRI | NULL    |       |
| sname   | varchar(30) | YES  |     | NULL    |       |
| address | varchar(30) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
3 rows in set (0.029 sec)

mysql> alter table supplier add email varchar(50(;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(' at line 1
mysql> alter table supplier add email varchar(50);
Query OK, 0 rows affected (0.748 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc supplier;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| suppid  | int         | NO   | PRI | NULL    |       |
| sname   | varchar(30) | YES  |     | NULL    |       |
| address | varchar(30) | YES  |     | NULL    |       |
| email   | varchar(50) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.030 sec)



USER RAJESH:
Microsoft Windows [Version 10.0.22631.4602]
(c) Microsoft Corporation. All rights reserved.

C:\Program Files\MySQL\MySQL Server 9.3\bin>mysql -h localhost -u rajesh -p
Enter password: *****
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 70
Server version: 9.3.0 MySQL Community Server - GPL

Copyright (c) 2000, 2025, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use inventory;
Database changed
mysql> desc supplier;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| suppid  | int         | NO   | PRI | NULL    |       |
| sname   | varchar(30) | YES  |     | NULL    |       |
| address | varchar(30) | YES  |     | NULL    |       |
| email   | varchar(50) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.186 sec)

mysql> show grants for'rajesh'@localhost;
+-------------------------------------------------------+
| Grants for rajesh@localhost                           |
+-------------------------------------------------------+
| GRANT USAGE ON *.* TO `rajesh`@`localhost`            |
| GRANT SELECT ON `inventory`.* TO `rajesh`@`localhost` |
+-------------------------------------------------------+
2 rows in set (0.148 sec)

