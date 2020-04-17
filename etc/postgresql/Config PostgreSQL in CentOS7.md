# Config PostgreSQL in CentOS7
It is no way to use `service postgresql-9.4 initdb` init PostgreSQL in CentOS7. I use following commends.
```
[root@my_computer ~]# systemctl enable postgresql-9.4
Created symlink from /etc/systemd/system/multi-user.target.wants/postgresql-9.4.service to /usr/lib/systemd/system/postgresql-9.4.service.
[root@my_computer ~]# /usr/pgsql-9.4/bin/postgres initdb
postgres                   postgresql94-check-db-dir  postgresql94-setup         
[root@my_computer ~]# /usr/pgsql-9.4/bin/postgresql94-setup initdb
Initializing database ... OK
[root@my_computer ~]# systemctl start postgresql-9.4
[root@second_computer ~]# su - postgres
-bash-4.2$ psql
psql (9.4.26)
Type "help" for help.

postgres=#
```
Now you can execute sql in the terminal.


EOF