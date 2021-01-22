Drupal Webserver - Ansible Role
=========

A complete, "ready-to-go", drupal website.
This contains:
- Drupal frontend
- Nginx & PHP backend
- PostgreSql database

This role is built to roll out existing webapplications. It uses already-made database dumps to provision new instances with the correct information and setup to instantly configure and provision a new instance.

Requirements
------------

This role is made to function on a CentOS/RHEL 8 machine.
This role requires a already made drupal website (sites directory), along with its database (databasedump)

Role Variables
--------------

| Variable             | Default          | Meaning                                                                                |
|----------------------|------------------|----------------------------------------------------------------------------------------|
| postgresUser         | drupaluser       | Username used to specify the owner of the postgres database                            |
| postgresPassword     | drupal           | Password used to authenticate the postgresUser                                         |
| postgresDatabasename | drupal           | Name for the postgres database used for drupal                                         |
| postgresDatabaseDump | databasedump.sql | The database backup-file, used to provision the database (Place in /ansible directory) |
| drupalDirname        | corona2020.local | Name used to specify the drupal website (in /var/www/html)                             |
| crtFile              | ca.crt           | The certificate used to enable the website with HTTPS                                  |
| keyFile              | ca.key           | The keyfile that goes along with the certificate                                       |
| enableHTTP           | true             | Allow traffic through HTTP                                                             |
| enableHTTPS          | true             | Allow traffic through HTTPS                                                            |

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: drupal_website_ansible, x: 42 }

License
-------

BSD
