# PostgreSQL switch database
In PosgreSQL there are several ways to switch database.

* Before connecting

Before connecting to server you can use following command to appoint the database you want to connect.
```
psql <database_name>
```
* Switch database

Use `\c` or `\connect` to switch the database.
```
postgres=# \c user
psql (8.4.20)
You are now connected to database "user".
```

EOF