# PostgreSQL dump database
It is easy to dump database by using `pg_dump` commend.

You need to switch to `postgres` role then execute follow commend to dump your database.
```
sudo -i -u postgres
pg_dump dbname > outfile
```

EOF