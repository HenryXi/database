# MySQL 8.0 enable remote access
Follow this [article](http://www.henryxi.com/install-mysql-in-centos) to download and install mysql. In this page I will
show you how to enable remote access.

1. After login, create new user with password.
```
mysql> CREATE USER 'root'@'%' IDENTIFIED BY 'rjyWzEz7A3=r66';
Query OK, 0 rows affected (0.08 sec)
```
2. Give the privileges
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
Query OK, 0 rows affected (0.10 sec)
```

EOF