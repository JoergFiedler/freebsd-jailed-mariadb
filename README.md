freebsd-jailed-mariadb
=========

This role provides a jailed MariaDB server.

You may configure the MariaDb server using the `my.cnf` you will find in the `templates` folder.

The role creates a ZFS dataset on an existing pool and mounts it to the jail. It is used to store the MariaDB database files.

Requirements
------------

This role is intent to be used with a fresh FreeBSD installation.

There is a Vagrant Box with providers for VirtualBox and EC2 you may use. You will find a sample project which uses this role [here](https://github.com/JoergFiedler/freebsd-ansible-demo).

Role Variables
--------------

##### jail_net_ip

The jail's ip address. No default value.

##### jail_net_if

The interface to which the jail's ip address is added. Default: `'lo0'`.

##### jail_name

The jail's name. Local part of the hostname. Default: `'{{ jail_net_ip }}'`.

##### jail_domain

The domain this jail belongs to. Domain part of the hostname. Default: `'darkcity'`.

##### mariadb_root_passwd

The root password that should be used to secure the MariaDB installation. Default: `'passwd'`.

##### mariadb_home

The directory in which MariaDB should store is files. Default: `'/home/mariadb'`.

##### host_mariadb_zfs_dataset

The ZFS dataset to use for MariaDB. If it does not exist it will be created. Make sure the pool already exists. Default: `'tank/mariadb'`.

##### host_mariadb_home

The directory on the host file system where the ZFS dataset is going to be mounted. Default: `'/home/mariadb'`.

Dependencies
------------

- [JoergFiedler.freebsd-jailed](https://galaxy.ansible.com/detail#/role/6599)

Example Playbook
----------------

    - { role: /Users/john/projects/freebsd-jailed-mariadb,
        tags: ['mariadb'],
        use_ssmtp: true,
        use_syslogd_server: true,
        jail_name: 'mariadb',
        jail_net_ip: '10.1.0.4' }¬

License
-------

BSD

Author Information
------------------

Any ideas to improve this project, please open an issue on Github. Thanks.

