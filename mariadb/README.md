# Mariadb install and maintanance role

## Description

This role is for deploying and maintaining a mariadb service and associated databases users and permissions.
For the time being it's only for local db connections.

## Testen on following OS

- Centos 7
- Ubuntu 18.04

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
    mariadb_databases:
      - { name: '1st_database', collation: 'utf8_general_ci', encoding: 'utf8' }
    mariadb_users:
      - { name: 'steven', password: 'P@ssword123', host: 'localhost', privileges: '*:ALL' }
  roles:
    - mariadb
```
