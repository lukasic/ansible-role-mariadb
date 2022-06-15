Role Name
=========

Simple Ansible MariaDB Role.


Changelog
---------

1.1.0

* Support Debian Bullseye and Ubuntu Jammy
* Add changelog

1.0.0

* Ansible Role for Debian Buster and Ubuntu Focal


Installation
------------

Using `ansible-galaxy`:

```bash
$ ansible-galaxy install lukasic.mariadb
```

Using `requirements.yml`:

```yaml
- src: lukasic.mariadb
```

Requirements
------------

Debian Buster / Ubuntu Focal or higher.


Role Variables
--------------

Parameters for `/etc/mysql/mariadb.conf.d/50-server.cnf`

```yaml
mariadb_server_params: []
```

MariaDB root passsword:

```yaml
mariadb_root_passwd: null
```

Databases and users to be created:

```yaml
mariadb_databases: []
mariadb_users: []
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: mariadb
  roles:
    - lukasic.mariadb
  vars:
    mariadb_server_params:
      - option: "sql_mode"
        section: "mysqld"
        value: "ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
      - option: "innodb_buffer_pool_size"
        section: "mysqld"
        value: "2G"
    mariadb_databases:
      - db1
    mariadb_users:
      - host: "%"
        name: "user_a"
        password: "supersecretpass"
        priv: "db1.*:ALL"
```

License
-------

WTFPL

Author Information
------------------

The role was created in 2020 by [Lukáš Kasič](https://github.com/lukasic).
