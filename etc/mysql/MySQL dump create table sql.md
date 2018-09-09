# MySQL dump create table sql
We can use `show create table <table_name>` to show the create table sql. The best way to export
the create table sql is using `mysqldump` command. Using following command to dump create tables 
sql of all tables in the `test_db` database.
```bash
mysqldump -u root -p <YOUR_DATABASE_NAME> --no-data > create_tables.sql 
```
Enter the password you will get the `create_tables.sql` in current directory. The create tables sql 
are all in the file `create_tables.sql`.

EOF