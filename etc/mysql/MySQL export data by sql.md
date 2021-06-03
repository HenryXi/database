# MySQL export data by sql
You can export data by using `mysqldump` command. Click [here](http://www.henryxi.com/mysql-export-data-with-where-condition) for more detail.

Another way to export data is using `mysql` command with `-e` parameter.

Using follow command to export user info to local file.
```
mysql -u USER -pPASSWORD -e "select * from database.user_info" > /tmp/user_info.txt
```

EOF