# Mariadb install and maintanance role

## Description

This role is for deploying and maintaining a mariadb service and associated databases users and permissions.
For the time being it's only for local db connections.

Role ERRORS when a root password is already set and is not equal to the 'mariadb_root_password' variable.(as it should)

## Testen on following OS

- Centos 7
- Centos 8
- Ubuntu 16.04
- Ubuntu 18.04
- Ubuntu 20.04
- OpenSuse Leap 15.1

## Variables

- mariadb_bind_address sets the bind addres for the mariadb service, it is defined in defaults as '127.0.0.1'.

 -mariadb_root_password sets/uses the mariadb root password, it is defined in defaults as '12345password' PLEASE USE THIS VARIABLE IN YOUR PLAYBOOK!! for abvious security reasons

## Database example usages

```yaml
mariadb_databases:
  - { dbname: '1st_database', collation: 'utf8_general_ci', encoding: 'utf8' }
  - { dbname: '2nd_database', collation: 'utf8_general_ci', encoding: 'utf8' }
  - { dbname: '3rd_database', collation: 'utf8_general_ci', encoding: 'utf8' }
```

```yaml
mariadb_databases:
  - dbname: '1st_database'
    collation: 'utf8_general_ci'
    encoding:  'utf8'
  - dbname: '2nd_database'
    collation: 'utf8_general_ci'
    encoding:  'utf8'
  - dbname: '3rd_database'
    collation: 'utf8_general_ci'
    encoding:  'utf8'
```

## Database User example usages

```yaml
mariadb_users:
  - { dbuser: 'steven', password: 'P@ssword123', host: 'localhost', privileges: '*.*:ALL' }
  - { dbuser: 'james', password: 'P@ssword456', host: 'localhost', privileges: '*.*:'SELECT,UPDATE,INSERT,DELETE,CREATE' }
  - { dbuser: 'tiger', password: 'P@ssword789', host: 'localhost', privileges: 'dennisdb.*:ALL,GRANT' }
```

```yaml
mariadb_users:
  - dbuser: 'steven'
    password: 'P@ssword123'
    host:  'localhost'
  - dbuser: 'james'
    password: 'P@ssword456'
    host:  'localhost'
  - dbuser: 'tiger'
    password: 'P@ssword789'
    host:  'localhost'
```

## Ansible-playbook example

```yaml
---
- hosts: testhost02
  become: yes
  vars:
    mariadb_root_password: '12345password'
    mariadb_databases:
      - { name: '1st_database', collation: 'utf8_general_ci', encoding: 'utf8' }
    mariadb_users:
      - { name: 'steven', password: 'P@ssword123', host: 'localhost', privileges: '*:ALL' }
  roles:
    - mariadb
```
