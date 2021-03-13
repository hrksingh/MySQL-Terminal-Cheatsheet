# MySQL-Terminal-Cheatsheet

1. Go to MySQL path  <code style="background:yellow;color:black"><strong>(cd C:\Program Files\MySQL\MySQL Server 8.0\bin)</strong></code>

2. \> mysql -uroot -p  <code style="background:yellow;color:black"><strong>--->(current user(root))</strong></code>

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

4. mysql> USE restapi <code style="background:yellow;color:black"><strong>--->(it select database to use)</strong></code>

5. mysql> SELECT DATABASE();  <code style="background:yellow;color:black"><strong>--->(it shows current using DB)</strong></code>
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
