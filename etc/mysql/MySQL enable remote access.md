# MySQL enable remote access
In this page I will show you how to make MySQL to support remote accessing. I assume you install MySQL in your
environment and local login successfully. Before remote accessing we need creating a database.

**1. Create a database**
```sql
mysql> create database db;
Query OK, 1 row affected (0.00 sec)
```

**2. Grant user access to db**

The SQL below means root can remote access any tables of any databases from any IP. You can change `*.* TO 'root'@'%'`
 to `<database_name>.<table_name> TO '<user_name>'@'<IP_address>'` when necessary.
```sql
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
Query OK, 0 rows affected, 1 warning (0.00 sec)
```

**3. Don't forget close firewall or add rule in firewall**

Use following command to close firewall.
```bash
[root@henry ~]# service iptables stop
iptables: Setting chains to policy ACCEPT: filter          [  OK  ]
iptables: Flushing firewall rules:                         [  OK  ]
iptables: Unloading modules:                               [  OK  ]
```
Use following command to add rule allow MySQL remote access.
```bash
[root@henry ~]# iptables -I INPUT -p tcp -m tcp --dport 3306 -j ACCEPT
[root@henry ~]# service iptables save
```

**4. Test remote access**
```bash
[root@virtual ~]# mysql -u root -p -h <your_IP_address> -P <your_mysql_port>
```