# MySQL-Terminal-Cheatsheet

1. Go to MySQL path  <code style="background:yellow;color:black"><strong>(cd C:\Program Files\MySQL\MySQL Server 8.0\bin)</strong></code>

2. ```mysql > mysql -uroot -p ```  <code style="background:yellow;color:black"><strong>--->(current user(root))</strong></code>

3. ```mysql SHOW DATABASES; ``` <code style="background:yellow;color:black"><strong>--->(show databases for that user)</strong></code>
```mysql
+--------------------+
| Database           |
+--------------------+
| demosql            |
| information_schema |
| mysql              |
| performance_schema |
| restapi            |
| sys                |
+--------------------+
```

4.```mysql  mysql> USE restapi ``` <code style="background:yellow;color:black"><strong>--->(it select database to use)</strong></code>

5.```mysql  mysql> SELECT DATABASE(); ```  <code style="background:yellow;color:black"><strong>--->(it shows current using DB)</strong></code>
```mysql
+------------+
| DATABASE() |
+------------+
| restapi    |
+------------+
```

6. ```mysql  mysql> SHOW TABLES; ```
```mysql
+--------------------+
| Tables_in_restapi  |
+--------------------+
| books              |
| hibernate_sequence |
+--------------------+
```

7. ```mysql mysql> Select * from books; ```
```mysql
+---------+-------------+-------------+------------+
| book_id | book_author | book_name   | book_price |
+---------+-------------+-------------+------------+
|                                                  |
|                  Demo Data                       |
|                                                  |
+---------+-------------+-------------+------------+
```

8. ```mysql  mysql> DESCRIBE books; ```
```mysql
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| book_id     | bigint       | NO   | PRI | NULL    | auto_increment |
| book_author | varchar(255) | YES  |     | NULL    |                |
| book_name   | varchar(255) | YES  |     | NULL    |                |
| book_price  | int          | NO   |     | NULL    |                |
+-------------+--------------+------+-----+---------+----------------+
```

9. Show the complete CREATE TABLE statement used by MySQL to create this table
```mysql

mysql> SHOW CREATE TABLE books \G
*************************** 1. row ***************************
       Table: books
Create Table: CREATE TABLE `books` (
  `book_id` bigint NOT NULL AUTO_INCREMENT,
  `book_author` varchar(255) DEFAULT NULL,
  `book_name` varchar(255) DEFAULT NULL,
  `book_price` int NOT NULL,
  PRIMARY KEY (`book_id`)
) ENGINE=InnoDB AUTO_INCREMENT=48 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci
```
