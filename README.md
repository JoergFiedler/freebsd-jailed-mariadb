freebsd-jailed-mariadb
=========

This role provides a jailed MariaDB server.

Requirements
------------

This role is intent to be used with a fresh FreeBSD installation.

There is a Vagrant Box with providers for VirtualBox and EC2 you may use. You will find a sample project which uses this role [here](https://github.com/JoergFiedler/freebsd-ansible-demo).

Role Variables
--------------

##### jail_net_ip

The jail's ip address. No default value.

##### jail_name

The jail's name. Local part of the hostname. Default: `'{{ jail_net_ip }}'`.

##### jail_domain

The domain the jail belongs to. Domain part of the hostname. Default: `'darkcity'`.

Dependencies
------------

- [JoergFiedler.freebsd-jail-host](https://galaxy.ansible.com/detail#/role/5827)

Example Playbook
----------------

License
-------

BSD

Author Information
------------------

Any ideas to improve this project, please open an issue on Github. Thanks.

