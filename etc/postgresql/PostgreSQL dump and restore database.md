# PostgreSQL dump and restore database
It is easy to dump database by using `pg_dump` commend.

You need to switch to `postgres` role then execute follow commend to dump your database.
```
sudo -i -u postgres
pg_dump dbname > outfile
```

After getting dump file, you can use `psql` to restore your database.
```
psql dbname < infile
```

EOF