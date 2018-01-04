# MySQL create multiple indexes in one sql
The statement of creating index on table will lock the table.It will cost a long time if you create multiple 
indexes in a big table. You can use `ALTER TABLE ...` to create or drop multiple indexes in one sql. The example
is here.

Every `CREATE INDEX...` statement will lock table.
```sql
-- two create index statement will lock table twice
CREATE UNIQUE INDEX users_user_name_uindex ON test_db.users (user_name);
CREATE UNIQUE INDEX users_address_uindex ON test_db.users (address);
```

Use `ALTER TABLE...` statement to create indexes will lock table only once.
```sql
ALTER TABLE test_db.users
  ADD UNIQUE INDEX users_user_name_uindex(user_name),
  ADD UNIQUE INDEX users_address_uindex(address);
```

The statement of drop multiple indexes
```sql
ALTER TABLE test_db.users
  DROP INDEX users_user_name_uindex,
  DROP INDEX users_address_uindex;
```
EOF