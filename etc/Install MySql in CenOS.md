# Install MySQL in CentOS
In this page I will show you how to install MySQL in CentOS. My environment is CenOS6, it is almost same steps to install
MySQL in other version of CentOS. We assume that you have install CentOS successfully. 

**1. Download yum repository packages**

You can find the repository file from [here](http://dev.mysql.com/downloads/repo/yum/). Choose the correct version
and download it with wget. My environment is CentOS6 I choose "Red Hat Enterprise Linux 6 / Oracle Linux 6 (Architecture Independent), RPM Package"
After clicking the button the page redirect to a page for login. On the bottom of the page you can see "No thanks, just start my download." link.
Copy the link and download repository packages with wget like following.
```bash
wget http://dev.mysql.com/get/mysql57-community-release-el6-9.noarch.rpm
```


**2. Install yum repository packages**

Install this file with `yum`
```bash
yum localinstall mysql57-community-release-el6-9.noarch.rpm 
```

**3. Install mysql-server with `yum` command**

```bash
yum install mysql-server
```
The output like following.
```bash
Loaded plugins: fastestmirror
Setting up Install Process
Loading mirror speeds from cached hostfile
Package mysql-server is obsoleted by mysql-community-server, trying to install mysql-community-server-5.7.16-1.el6.x86_64 instead
Resolving Dependencies
--> Running transaction check
---> Package mysql-community-server.x86_64 0:5.7.16-1.el6 will be installed
--> Processing Dependency: mysql-community-client(x86-64) >= 5.7.9 for package: mysql-community-server-5.7.16-1.el6.x86_64
--> Running transaction check
---> Package mysql-community-client.x86_64 0:5.7.16-1.el6 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=====================================================================================================================
 Package                            Arch               Version                   Repository                     Size
=====================================================================================================================
Installing:
 mysql-community-server             x86_64             5.7.16-1.el6              mysql57-community             144 M
Installing for dependencies:
 mysql-community-client             x86_64             5.7.16-1.el6              mysql57-community              23 M

Transaction Summary
=====================================================================================================================
Install       2 Package(s)

Total download size: 166 M
Installed size: 831 M
Is this ok [y/N]:
```
Press "y" and wait for the installation finished.
**4. Start mysqld service**

```bash
service mysqld service
```
If you get the output like following it means you have install mysql successfully.
```bash
Starting mysqld:                                           [  OK  ]
```