# MySQL export data with where condition
[Last](http://www.henryxi.com/mysql-export-import-sql-file-in-command-line) blog I have showed you how to export data from database. 
If you don't want to dump all data from database you can add `--where` parameter. If you want dump user info where age bigger 
then 27 the command is like following.
```bash
$ mysqldump -u root -p user_db user_tb --where="age>27"> users.sql
```
If you have multiple conditions the command is like following.
```bash
$ mysqldump -u root -p user_db user_tb --where="age>27 and name = 'henry'" > users.sql
```
Don't forget to use **double quotation marks** append `--where=`. 