freebsd-jailed-mariadb
=========

This role provides a jailed MariaDB server.

You may configure the MariaDb server using `my.cnf` file which you will find in the `templates` folder.

Requirements
------------

This role is intent to be used with a fresh FreeBSD installation.

There is a Vagrant Box with providers for VirtualBox and EC2 you may use. You will find a sample project which uses this role [here](https://github.com/JoergFiedler/freebsd-ansible-demo).

Role Variables
--------------

##### mariadb_root_passwd

The hashed root password that should be used to secure the MariaDB installation. The default password is `passwd` you may want to change that. Default: `'59c70da2f3e3a5bdf46b68f5c8b8f25762bccef0'`.

##### mariadb_home

The directory in which MariaDB should store is files. Default: `'/srv/mariadb'`.

##### host_mariadb_zfs_dataset

The ZFS dataset to use for MariaDB. If it does not exist it will be created. Make sure the pool already exists. Default: `'tank/mariadb'`.

##### host_mariadb_zfs_dir

The directory on the host file system where the ZFS dataset is going to be mounted. Default: `'/srv/mariadb'`.

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

