# MySQL show open transaction
Once I got stuck while executing sql. I checked the process with the following command
```
SHOW FULL PROCESSLIST  
```
But all processes are in sleep state. I'm guessing that some transaction locks some rows.
I use below sql to view all transaction information.
```sql
SELECT * FROM information_schema.innodb_trx
```
Fortunately I did find an uncommitted transaction. After I kill this transaction with the kill command, my sql can be executed successfully

EOF