# Store UUID in MySql
There are two ways to store UUID in MySQL. The one is save it as varchar(36), the other is save is as varbinary(16).
The first way is easy for developer, just set UUID string in field of entity and insert it into database. But the second
way can save disk space and quick. 
 
**use varchar(36)**

It is easy to save and query id from database for developer.
```sql
CREATE TABLE `test_varchar_table` (
  `id` varchar(36) NOT NULL,
  `name` varchar(40) NOT NULL
)

INSERT INTO test_varchar_table SET id='8db2efb56a624c2f92e36eb0ee854221', name='Henry';
```
When you need query this record
```sql
select * from test_varchar_table;
```


**use varbinary(16)**

When you save this record you need convert UUID string to hexadecimal.
```sql
CREATE TABLE `test_varbinary_table` (
  `id` VARBINARY(16) NOT NULL,
  `name` varchar(40) NOT NULL
);

INSERT INTO test_varbinary_table SET id=0x8db2efb56a624c2f92e36eb0ee854221, name='Henry';
```
When you need query this record you need convert hexadecimal to string.
```sql
select hex(id) ,name from test_varbinary_table;
```