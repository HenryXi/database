# PostgreSQL show databases
In PostgreSQL there are two ways to list all databases.

* Use command

`\list` or `\l` can list all databases. In my environment the output
is like following.
```
user=# \l
                              List of databases
   Name    |  Owner   | Encoding  | Collation | Ctype |   Access privileges   
-----------+----------+-----------+-----------+-------+-----------------------
 user      | postgres | SQL_ASCII | C         | C     | 
 postgres  | postgres | SQL_ASCII | C         | C     | 
 template0 | postgres | SQL_ASCII | C         | C     | =c/postgres
                                                      : postgres=CTc/postgres
 template1 | postgres | SQL_ASCII | C         | C     | =c/postgres
                                                      : postgres=CTc/postgres
(4 rows)
```
* Use sql

You can also use sql to show the name of databases.
```
blog=# SELECT datname FROM pg_database WHERE datistemplate = false;
 datname  
----------
 postgres
 user
(2 rows)
```

EOF