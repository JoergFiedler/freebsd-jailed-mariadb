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

##### mariadb_home

The directory in which MariaDB should store is files. Default: `'/srv/mariadb'`.

##### mariadb_server_pkg

The package name of the server package (which version to install). Default `'mariadb103-server'`.

##### host_mariadb_zfs_dataset

The ZFS dataset to use for MariaDB. If it does not exist it will be created. Make sure the pool already exists. Default: `'tank/mariadb'`.

##### host_mariadb_zfs_dir

The directory on the host file system where the ZFS dataset is going to be mounted. Default: `'/srv/mariadb'`.

Dependencies
------------

- [JoergFiedler.freebsd-jailed](https://galaxy.ansible.com/joergfiedler/freebsd-jailed)

Example Playbook
----------------

    - hosts: all
      become: true
    
      vars:
        ansible_python_interpreter: '/usr/local/bin/python2.7'
    
      tasks:
        - include_role:
            name: 'JoergFiedler.freebsd-jailed-mariadb'
          vars:
            jail_freebsd_release: '11.2-RELEASE'
            jail_name: 'mariadb'
            jail_net_ip: '10.1.0.10'

License
-------

BSD

Author Information
------------------

Any ideas to improve this project, please open an issue on Github. Thanks.

