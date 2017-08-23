# MySQL show indexes for table
There are several ways to show indexes for a table in MySQL. Let's say you have create the table in your database.
The schema of table is here.
```sql
CREATE TABLE `users` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `user_name` varchar(50) DEFAULT NULL,
  `password` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `users_user_name_index` (`user_name`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1
```


**show index detail**
```sql
mysql> show index from users;
+-------+------------+-----------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
| Table | Non_unique | Key_name              | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment |
+-------+------------+-----------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
| users |          0 | PRIMARY               |            1 | id          | A         |         100 |     NULL | NULL   |      | BTREE      |         |               |
| users |          1 | users_user_name_index |            1 | user_name   | A         |          96 |     NULL | NULL   | YES  | BTREE      |         |               |
+-------+------------+-----------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
```

**show create table sql**
```sql
mysql> show create table users;
+-------+-------------------------------------------------------------+
| Table | Create Table                                                |
+-------+-------------------------------------------------------------+
| users | CREATE TABLE `users` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `user_name` varchar(50) DEFAULT NULL,
  `password` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `users_user_name_index` (`user_name`)
) ENGINE=InnoDB AUTO_INCREMENT=302 DEFAULT CHARSET=latin1 |
+-------+-------------------------------------------------------------+
```

EOF