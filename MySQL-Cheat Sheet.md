<span style="color:red"><Strong><h1>MySQL-Terminal-Cheatsheet</h1></strong></span> 

1. Go to MySQL path  
```cmd 
cd C:\Program Files\MySQL\MySQL Server 8.0\bin
```

2. sign-in with user -->  current user here (root)
```cmd
>mysql -uroot -p   
```

3. show databases for that user
```mysql
mysql> SHOW DATABASES;

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

4. It select database to use
```mysql
mysql> USE restapi;
```

5. It shows current using DB
```mysql
mysql> SELECT DATABASE();

+------------+
| DATABASE() |
+------------+
| restapi    |
+------------+
```

6. Show all tables in Database
```mysql
mysql> SHOW TABLES; 

+--------------------+
| Tables_in_restapi  |
+--------------------+
| books              |
| hibernate_sequence |
+--------------------+
```

7. Select statement
```mysql
mysql> Select * from books;

+---------+-------------+-------------+------------+
| book_id | book_author | book_name   | book_price |
+---------+-------------+-------------+------------+
|                                                  |
|                  Demo Data                       |
|                                                  |
+---------+-------------+-------------+------------+
```

8. Shows Metadata
```mysql
 mysql> DESCRIBE books; 
 
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
 ```cmd
  mysql> INSERT INTO products VALUES (1001, 'PEN', 'Pen Red', 5000, 1.23);
 ```  
 
12. Insert multiple rows in one command and Inserting NULL to the auto_increment column results in max_value + 1
  ```cmd
  mysql> INSERT INTO products VALUES
         (NULL, 'PEN', 'Pen Blue',  8000, 1.25),
         (NULL, 'PEN', 'Pen Black', 2000, 1.25);
   ``` 
   
13. Remove the last row
 ```cmd
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

<Strong>via the "source" command in a MySQL client</strong>

```mysql
  mysql> source d:/myProject/load_products.sql
     -- Use Unix-style forward slash (/) as directory separator
 ```
 
<h1> Backup and Restore </h1>
18. Backup

>Backup: Before we conclude this example, let's run the mysqldump utility program to dump out (backup) the entire restapi database.

The SYNTAX for the mysqldump utility program is as follows:


```mysql
-- Dump selected databases with --databases option
> mysqldump -u username -p --databases database1Name [database2Name ...] > backupFile.sql

-- Dump all databases in the server with --all-databases option, except mysql.user table (for security)
> mysqldump -u root -p --all-databases --ignore-table=mysql.user > backupServer.sql
  
-- Dump all the tables of a particular database
> mysqldump -u username -p databaseName > backupFile.sql

-- Dump selected tables of a particular database
> mysqldump -u username -p databaseName table1Name [table2Name ...] > backupFile.sql
```
---
```mysql
-- Start a NEW "cmd"
> cd path-to-mysql-bin
> mysqldump -u root -p --databases restapi > "d:\myProject\backup_restapi.sql"
```
* Study the output file, which contains CREATE DATABASE, CREATE TABLE and INSERT statements to re-create the tables dumped.

19. Restore:

The utility mysqldump produces a SQL script (consisting of CREATE TABLE and INSERT commands to re-create the tables and loading their data). You can restore from the backup by running the script either:

```mysql

    -- Start a MySQL client
    mysql> source d:/myProject/backup_southwind.sql
       -- Provide absolute or relative filename of the script
       -- Use Unix-style forward slash (/) as path separator
       
   ```


20. For more details and examples <a href="https://www3.ntu.edu.sg/home/ehchua/programming/sql/MySQL_Beginner.html" title="ntu">visit this</a>

