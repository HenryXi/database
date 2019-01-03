# MySQL change data directory
The default data directory of MySQL is `/var/lib/mysql`. If there is no disk space for this directory we need to move data
to another directory(another fileSystem). In my environment I install MySQL by yum command. The `/var/lib/mysql` directory
is mounted on `/` and there is no more space for data. I change data directory by using these following commands.
```bash
[root@virtual ~]# service mysqld stop
Stopping mysqld:                                           [  OK  ]
[root@virtual ~]# mkdir mysql_data
[root@virtual ~]# mv /var/lib/mysql/ ~/mysql_data/
[root@virtual ~]# ln -s ~/mysql_data/mysql /var/lib/
[root@virtual ~]# service mysqld start
Starting mysqld:                                           [  OK  ]
```

EOF