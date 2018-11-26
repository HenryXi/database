# PostgreSQL display result vertically
In MySQL we can add `\G` in the end of sql to show the result vertically. In PostgreSQL you need to enter `\x` to show
the result vertically. It is a toggle. Example sql is here.
```sql
postgres=# select id,update_time from book limit 2;
   id    |       update_time       
---------+-------------------------
 4919407 | 2017-10-31 15:10:54.554
 3242345 | 2017-10-31 15:10:54.564
(2 rows)

postgres=# \x
Expanded display is on.
postgres=# select id,update_time from book limit 2;
-[ RECORD 1 ]------------------------
id          | 4919407
update_time | 2017-10-31 15:10:54.554
-[ RECORD 2 ]------------------------
id          | 3242345
update_time | 2017-10-31 15:10:54.564

postgres=# \x
Expanded display is off.
postgres=# select id,update_time from book limit 2;
   id    |       update_time       
---------+-------------------------
 4919407 | 2017-10-31 15:10:54.554
 3242345 | 2017-10-31 15:10:54.564
(2 rows)
```

EOF