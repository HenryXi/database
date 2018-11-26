# Your password does not satisfy the current policy requirements
When you see "Your password does not satisfy the current policy requirements" error message that means your password
is not safe. MySQL use `validate_password` plugin to test passwords and improve security. There are 3 levels in 
`validate_password_policy`. You can check the value of it by using following command.
```sql
mysql> SHOW VARIABLES LIKE 'validate_password%';
+--------------------------------------+--------+
| Variable_name                        | Value  |
+--------------------------------------+--------+
| validate_password_check_user_name    | OFF    |
| validate_password_dictionary_file    |        |
| validate_password_length             | 8      |
| validate_password_mixed_case_count   | 1      |
| validate_password_number_count       | 1      |
| validate_password_policy             | MEDIUM |
| validate_password_special_char_count | 1      |
+--------------------------------------+--------+
7 rows in set (0.02 sec)
```

**Three levels of password checking**

|Policy|Tests Performed|
|:-----|:--------------|
|0 or LOW|tests password length only. Passwords must be at least 8 characters long.|
|1 or MEDIUM|adds the conditions that passwords must contain at least 1 numeric character, 1 lowercase character, 1 uppercase character, and 1 special (nonalphanumeric) character.|
|2 or STRONG|adds the condition that password substrings of length 4 or longer must not match words in the dictionary file, if one has been specified.|

You can use following command to change the level of password checking.
```sql
mysql> set global validate_password_policy=0;
Query OK, 0 rows affected (0.00 sec)
```

**Remove `validate_password` plugin (NOT RECOMMEND)**

There are many plugins in MySQL use following command to show all plugins.
```sql
mysql> SHOW PLUGINS\G
*************************** 1. row ***************************
   Name: binlog
 Status: ACTIVE
   Type: STORAGE ENGINE
Library: NULL
License: GPL
*************************** 2. row ***************************
   Name: mysql_native_password
 Status: ACTIVE
   Type: AUTHENTICATION
Library: NULL
License: GPL
*************************** 3. row ***************************
   Name: sha256_password
 Status: ACTIVE
   Type: AUTHENTICATION
Library: NULL
License: GPL

...
...
...

*************************** 45. row ***************************
   Name: validate_password
 Status: ACTIVE
   Type: VALIDATE PASSWORD
Library: validate_password.so
License: GPL
45 rows in set (0.00 sec)

```
If you install MySQL just for testing. You can remove `validate_password` plugin by using following command.
```sql
mysql> uninstall plugin validate_password;
Query OK, 0 rows affected (0.02 sec)
```

**UPDATE** for MySQL 8.0 use `UNINSTALL COMPONENT 'file://component_validate_password';` to remove this plugin.