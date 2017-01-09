# MySQL export import sql file in command line
In this page I will show you how to export and import sql file in command line. I assume you have install MySQL in 
your environment, the database name is "user_db", the table is "users_tb", the password of this database is "password" and the username is "root".

## Export data into sql file

If you want export all tables in your database use following command.
```sql
$ mysqldump -u root -p users > users.sql
```
If you want only export a specific table (or tables) you can do like this.
```sql
$ mysqldump -u root -p users_tb > users_tb.sql
```

## Import sql file into database 

Let's say you have export data from database successfully. The name of sql file is "users_tb.sql". The following command
will import data into database.
```sql
$ mysql -u root -p user_db < data.sql
```

All commands mentioned above works when you install MySQL in your **local** machine. If you want **remote** export or import
don't forget use `-p` argument.