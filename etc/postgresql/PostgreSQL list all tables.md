# PostgreSQL list all tables
Use `\d` or `\d+` in `psql` command to show all tables. `\d+` will show additional detail of tables; 
```bash
blog=$ \d
             List of relations
 Schema |    Name           |   Type   |  Owner   
--------+-------------------+----------+----------
 public | user              | table    | postgres
 public | company           | table    | postgres
 public | address           | table    | postgres
 public | address_id_seq    | sequence | postgres
(4 rows)

blog=$ \d+
                          List of relations
 Schema |    Name        |   Type   |  Owner   |    Size    | Description 
--------+----------------+----------+----------+------------+-------------
 public | user           | table    | postgres | 8192 bytes | 
 public | company        | table    | postgres | 8848 kB    | 
 public | address        | table    | postgres | 34 MB      | 
 public | address_id_seq | sequence | postgres | 8192 bytes | 
(4 rows) 
```

<p align="center">-----EOF-----</p>