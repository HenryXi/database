# MySQL delete duplicate rows
Duplicate rows will be in you table when you don't use unique key for some reason. In this page I will show you
how to remove duplicate rows in MySQL. Let's say the schema of user table is like following.
```sql
CREATE TABLE `users` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `user_name` varchar(50) DEFAULT NULL,
  `password` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=302 DEFAULT CHARSET=latin1
```
Show how many duplicate rows in the table;
```sql
select count(*),user_name from users GROUP BY user_name having count(*) > 1;
```
Delete the duplicate rows.
```sql
delete from users USING users, users u where u.id>users.id and u.user_name=users.user_name;
```

EOF
