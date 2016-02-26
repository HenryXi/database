# Install and configure postgresql on linux

PostgreSQL, simply "Postgres" for short, is an object-relational database
management system (ORDBMS). PostgreSQL is able to run on many operating systems
including Linux, FreeBSD, OS X, Solaris, and Microsoft Windows. In this blog I
will show you how to install and configure PostgreSQL on Linux(CentOS 6 x86).

1. There are two ways to download and install PostgreSQL.
    * Download RPMs directly from [official website](http://yum.postgresql.org/rpmchart.php) and install.(**NOT RECOMMEND**)

        Choose the version you want to install. For example my environment is CentOS 6 x86, so the right version is [http://yum.postgresql.org/9.4/redhat/rhel-6-i386/repoview/](http://yum.postgresql.org/9.4/redhat/rhel-6-i386/repoview/)
        click [PostgreSQL Database Server 9.4 PGDG](http://yum.postgresql.org/9.4/redhat/rhel-6-i386/repoview/postgresqldbserver94.group.html)
        you will see four RPMs. Download and install them(you have to install them in right order or you will get failure).
        ```
            wget http://yum.postgresql.org/9.4/redhat/rhel-6-i386/postgresql94-libs-9.4.6-1PGDG.rhel6.i686.rpm
            wget http://yum.postgresql.org/9.4/redhat/rhel-6-i386/postgresql94-9.4.6-1PGDG.rhel6.i686.rpm
            wget http://yum.postgresql.org/9.4/redhat/rhel-6-i386/postgresql94-server-9.4.6-1PGDG.rhel6.i686.rpm
            wget http://yum.postgresql.org/9.4/redhat/rhel-6-i386/postgresql94-contrib-9.4.6-1PGDG.rhel6.i686.rpm

        ```
        install them
        ```
            sudo yum localinstall postgresql94-libs-9.4.6-1PGDG.rhel6.i686.rpm postgresql94-9.4.6-1PGDG.rhel6.i686.rpm postgresql94-server-9.4.6-1PGDG.rhel6.i686.rpm postgresql94-contrib-9.4.6-1PGDG.rhel6.i686.rpm
        ```
    * Change your yum Repository use ``yum install`` command to install.

        I DO NOT RECOMMEND download RPMs directly and install, because you have to download them one by one and install them in right order.
         Change your yum Repository and use one line command can install PostgreSQL easily.
        use ``yum list 'postgresql*'`` to check available version.
        However, unfortunately, there is only one version(8.4) in my environment(CentOS 6 x86).
        ```
            postgresql.i686                     8.4.20-4.el6_7               updates
            postgresql-contrib.i686             8.4.20-4.el6_7               updates
            postgresql-devel.i686               8.4.20-4.el6_7               updates
            postgresql-docs.i686                8.4.20-4.el6_7               updates
            postgresql-jdbc.noarch              8.4.704-2.el6                base
            postgresql-libs.i686                8.4.20-4.el6_7               updates
            postgresql-odbc.i686                08.04.0200-1.el6             base
            postgresql-plperl.i686              8.4.20-4.el6_7               updates
            postgresql-plpython.i686            8.4.20-4.el6_7               updates
            postgresql-pltcl.i686               8.4.20-4.el6_7               updates
            postgresql-server.i686              8.4.20-4.el6_7               updates
            postgresql-test.i686                8.4.20-4.el6_7               updates
        ```
        In order to install 9.4 version we have to configure our YUM repository
        edit distributions .repo file append a line. That means do not use default Repository download and install PostgreSQL.
        ```
            exclude=postgresql*
        ```
        On Fedora: /etc/yum.repos.d/fedora.repo and /etc/yum.repos.d/fedora-updates.repo, [fedora] sections

        On CentOS: /etc/yum.repos.d/CentOS-Base.repo, [base] and [updates] sections

        On Red Hat: /etc/yum/pluginconf.d/rhnplugin.conf [main] section

        Browse [http://yum.postgresql.org/repopackages.php](http://yum.postgresql.org/repopackages.php) and find correct RPM. Here we use 9.4 on CentOS 6 x86.

        ```
            yum localinstall https://download.postgresql.org/pub/repos/yum/9.4/redhat/rhel-6-i386/pgdg-centos94-9.4-2.noarch.rpm
        ```
        List available packages again
        ```
            yum list 'postgresql*'
        ```
        now we have 9.4 version
        ```
            postgresql94.i686                       9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-contrib.i686               9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-debuginfo.i686             9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-devel.i686                 9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-docs.i686                  9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-jdbc.i686                  9.3.1101-1PGDG.rhel6              pgdg94
            postgresql94-jdbc-debuginfo.i686        9.3.1101-1PGDG.rhel6              pgdg94
            postgresql94-libs.i686                  9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-odbc.i686                  09.03.0400-1PGDG.rhel6            pgdg94
            postgresql94-odbc-debuginfo.i686        09.03.0400-1PGDG.rhel6            pgdg94
            postgresql94-plperl.i686                9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-plpython.i686              9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-pltcl.i686                 9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-python.i686                4.1.1-2PGDG.rhel6                 pgdg94
            postgresql94-python-debuginfo.i686      4.1.1-2PGDG.rhel6                 pgdg94
            postgresql94-server.i686                9.4.6-1PGDG.rhel6                 pgdg94
            postgresql94-tcl.i686                   2.1.1-1.rhel6                     pgdg94
            postgresql94-tcl-debuginfo.i686         2.1.1-1.rhel6                     pgdg94
            postgresql94-test.i686                  9.4.6-1PGDG.rhel6                 pgdg94
        ```
        use yum command to install it
        ```
            yum install postgresql94-server
        ```
2. Configure PostgreSQL on linux after installing.

    Init DB and start service
    ```
        service postgresql-9.4 initdb
        service postgresql-9.4 start
    ```
    **Enable local login with password**

    After installing PostgreSQL we can use default user ``postgres`` to login without password.(Current Authentication
    is Peer Authentication, we will change it to Password Authentication later.)
    ```
        sudo -u postgres psql template1
    ```
    What we want is Password Authentication, so we set the password for user postgres. Then login out(ctrl+D)
    ```
        ALTER USER postgres with encrypted password 'your_password'
    ```
    Now change Authentication to Password Authentication. Edit ``pg_hba.conf``
    ```
        vi /var/lib/pgsql/9.4/data/pg_hba.conf
    ```
    change it as following, "md5" means allow user login with password.
    ```
        # "local" is for Unix domain socket connections only
        local   all             all                                     md5
    ```
    restart PostgreSQL
    ```
        service postgresql-9.4 restart
    ```
    now you can login as postgres with password
    ```
        psql -U postgres
    ```
    **Enable remote login**
    edit ``pg_hba.conf`` again, change as following(change ``192.168.1.8`` to your IP address, and
    change Authentication to md5)
    ```
        # IPv4 local connections:
        host    all             all             127.0.0.1/32            ident
        host    all             all             192.168.1.8/32          md5
    ```
    edit ``postgresql.conf``, change as following.
    ```
        listen_addresses ='*'               # what IP address(es) to listen on;
    ```
    restart PostgreSQL
    ```
        service postgresql-9.4 restart
    ```
    now you can use PostgreSQL with remote connection.