# Enable PostgreSQL remote access
Following these steps to enable PostgreSQL remote access.

1. change `pg_hba.conf`, add following line
```
host    all             all             0.0.0.0/0                   md5
host    all             all             10.232.29.111/32            md5
```
2. add `listen_addresses='*'` in postgresql.conf.

3. stop firewall or add ip rules.
```
systemctl stop firewalld
```

EOF