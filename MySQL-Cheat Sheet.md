# MySQL-Terminal-Cheatsheet

1. Go to MySQL path   >(cd C:\Program Files\MySQL\MySQL Server 8.0\bin)

2. \> mysql -uroot -p    >(current user(root))

3. SHOW DATABASES;    >(show databases for that user)
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

4. mysql> USE restapi    >(it select database to use)

5. mysql> SELECT DATABASE();     >(it shows current using DB)
```mysql
+------------+
| DATABASE() |
+------------+
| restapi    |
+------------+
```

6. mysql> SHOW TABLES;
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
