# MySQL-Terminal-Cheatsheet

1. Go to MySQL path  <code style="background:yellow;color:black"><strong>(cd C:\Program Files\MySQL\MySQL Server 8.0\bin)</strong></code>

2. \>mysql -uroot -p   <code style="background:yellow;color:black"><strong>--->(current user(root))</strong></code>

3. SHOW DATABASES;  <code style="background:yellow;color:black"><strong>--->(show databases for that user)</strong></code>
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

4.mysql> USE restapi  <code style="background:yellow;color:black"><strong>--->(it select database to use)</strong></code>

5.mysql> SELECT DATABASE();   <code style="background:yellow;color:black"><strong>--->(it shows current using DB)</strong></code>
```mysql
+------------+
| DATABASE() |
+------------+
| restapi    |
+------------+
```

6.  mysql> SHOW TABLES; 
```mysql
+--------------------+
| Tables_in_restapi  |
+--------------------+
| books              |
| hibernate_sequence |
+--------------------+
```

7. mysql> Select * from books; 
```mysql
+---------+-------------+-------------+------------+
| book_id | book_author | book_name   | book_price |
+---------+-------------+-------------+------------+
|                                                  |
|                  Demo Data                       |
|                                                  |
+---------+-------------+-------------+------------+
```

8. mysql> DESCRIBE books; 
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

11. Insert a row with all the column values
 ```bash
  mysql> INSERT INTO products VALUES (1001, 'PEN', 'Pen Red', 5000, 1.23);
 ```  
 
12. Insert multiple rows in one command and Inserting NULL to the auto_increment column results in max_value + 1
  ```bash
  mysql> INSERT INTO products VALUES
         (NULL, 'PEN', 'Pen Blue',  8000, 1.25),
         (NULL, 'PEN', 'Pen Black', 2000, 1.25);
   ``` 
   
13. Remove the last row
 ```bash
mysql> DELETE FROM products WHERE productID = 1006;
```

14. you can SELECT an expression or evaluate a built-in function.
```mysql
mysql> SELECT NOW();
+---------------------+
| NOW()               |
+---------------------+
| 2021-03-13 18:09:00 |
+---------------------+
```

15. You can load the raw data into the products table as follows:
>make sure you have csv file ready with data on location
```mysql 
mysql> LOAD DATA LOCAL INFILE 'd:/myProject/products_in.csv' INTO TABLE products
         COLUMNS TERMINATED BY ','
         LINES TERMINATED BY '\r\n';
   ```

16. SELECT ... INTO OUTFILE ...

  Complimenting LOAD DATA command, you can use SELECT ... INTO OUTFILE fileName FROM tableName to export data from a table to a text file. For example,

```mysql
mysql> SELECT * FROM products INTO OUTFILE 'd:/myProject/products_out.csv' 
         COLUMNS TERMINATED BY ','
         LINES TERMINATED BY '\r\n';
   ```
   
17. Running a SQL Script
 
Instead of manually entering each of the SQL statements, you can keep many SQL statements in a text file, called SQL script, and run the script. For example, use a programming text editor to prepare the following script and save as "load_products.sql" under "d:\myProject"

```mysql
DELETE FROM products;
INSERT INTO products VALUES (2001, 'PEC', 'Pencil 3B', 500, 0.52),
                            (NULL, 'PEC', 'Pencil 4B', 200, 0.62),
                            (NULL, 'PEC', 'Pencil 5B', 100, 0.73),
                            (NULL, 'PEC', 'Pencil 6B', 500, 0.47);
SELECT * FROM products;
```

via the "source" command in a MySQL client



    ```mysql
    mysql> source d:/myProject/load_products.sql
       -- Use Unix-style forward slash (/) as directory separator
     ```
