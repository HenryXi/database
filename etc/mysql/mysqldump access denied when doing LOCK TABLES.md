# mysqldump access denied when doing LOCK TABLES
When I try to dump the table with the `mysqldump` command I got the error message. The dump command and the 
 error message are here.
```
> mysqldump -h my_host -u db_username -p my_dbname my_table__name > table.sql
mysqldump: Got error: 1044: Access denied for user 'db_username'@'my_host' to database 'my_dbname' when doing LOCK TABLES
```

After contacting the DBA I know that I do not have the permission to lock the table. As I don't care about the timeliness
of data, I use `--skip-lock-tables` parameter to skip to lock the table. I use following command export the table
successfully.
```
> mysqldump -h my_host -u db_username -p my_dbname my_table__name --skip-lock-tables > table.sql
```

EOF