# First time login MySQL after installation
In last [blog](http://www.henryxi.com/install-mysql-in-centos) I have introduced how to install MySQL in CentOS. In
this page I will show you how to login MySQL for the first time.

**1. Start MySQL service after installation**

```bash
[root@henry ~]# service mysqld start
Starting mysqld:                                           [  OK  ]
```

**2. Find the temporary password**

```bash
[root@henry ~]# sudo grep 'temporary password' /var/log/mysqld.log
2016-11-28T04:59:11.415303Z 1 [Note] A temporary password is generated for root@localhost: N%mSdQFGn6.B
```

**3. Login with password**

```bash
[root@henry ~]# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.7.16

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

**4. Change the password**
```bash
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'rjyWzEz7A3=r66';
```

**5. Disable validate_password plugin(if needed)**

If you want use simple password you can set password policy to low. Use `SET GLOBAL validate_password_policy=LOW;` or
remove this plugin by following command. 
```bash
mysql> uninstall plugin validate_password;
```
**UPDATE** for MySQL 8.0 use `UNINSTALL COMPONENT 'file://component_validate_password';` to remove this plugin.

EOF