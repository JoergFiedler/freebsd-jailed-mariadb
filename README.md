freebsd-jailed-mariadb
=========

[![Build Status](https://travis-ci.org/JoergFiedler/freebsd-jailed-mariadb.svg?branch=master)](https://travis-ci.org/JoergFiedler/freebsd-jailed-mariadb)

This role provides a jailed MariaDB server.

You may configure the MariaDb server using the `my.cnf` you will find in the `templates` folder.

The role creates a ZFS dataset on an existing pool and mounts it to the jail. It is used to store the MariaDB database files.

Requirements
------------

This role is intent to be used with a fresh FreeBSD installation.

Role Variables
--------------

##### mariadb_root_passwd

The root password that should be used to secure the MariaDB installation. Default: `'passwd'`.

##### mariadb_backup_user

The user name for backup user. It has read permissions to all databases to perform backup. Database content is stored in `{{ mariadb_home }}` folder. On file per database. The file is zipped. Default: `'no_root_user'`

##### mariadb_backup_user_passwd

The password for backup user. Default: `'passwd'`

##### mariadb_home

The directory in which MariaDB should store is files. Default: `'/srv/mariadb'`.

##### mariadb_server_pkg

The package name of the server package (which version to install). Default `'mariadb103-server'`.

##### host_mariadb_zfs_dataset

The ZFS dataset to use for MariaDB. If it does not exist it will be created. Make sure the pool already exists. Default: `'{{ host_srv_dataset }}/mariadb'`.

##### host_mariadb_zfs_dir

The directory on the host file system where the ZFS dataset is going to be mounted. Default: `'{{ host_srv_dir }}/mariadb'`.

Dependencies
------------

- [JoergFiedler.freebsd-jailed](https://galaxy.ansible.com/joergfiedler/freebsd-jailed)

Example Playbook
----------------

    - hosts: all
      become: true
    
      tasks:
        - import_role:
            name: 'JoergFiedler.freebsd-jail-host'
        - include_role:
            name: 'JoergFiedler.freebsd-jailed-mariadb'
          vars:
            jail_net_ip: '10.1.0.10'
            jail_name: 'mariadb'

License
-------

BSD

Author Information
------------------

Any ideas to improve this project, please open an issue on Github. Thanks.

