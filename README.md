Drupal Webserver - Ansible Role
=========

A complete, "ready-to-go", drupal website.
This contains:
- Drupal frontend
- Nginx & PHP backend
- PostgreSql database

This role is built to roll out existing webapplications. It uses already-made database dumps to provision new instances with the correct information and setup to instantly configure and provision a new instance.
This role can be very usefull when trying to setup a high available cluster of webservers.

Requirements
------------

- This role is made to function on a CentOS/RHEL 8 machine.
- This role requires a already made drupal website (sites directory), along with its database (databasedump)
- A CA certificate is required in order to allow HTTPS connection

How to use
------------

Once a drupal website has been made, this role can be used to roll out the website to different instances, using Nginx & PHP.
First of all, copy the "sites" directory (drupal) into the "drupalPreset" folder, within the role's directory.
After that, a database dump should be made, and copied into the role's "drupalPreset" directory. (for more info on how to do this, follow these guidelines: https://www.postgresql.org/docs/9.1/backup-dump.html
If you wish to use HTTPS instead of HTTP (or both), a certificate and key should be placed in the "certs" folder, within the role's directory.

After completing the playbook and configuring the variables, ansible can run the playbook and setup your drupal website with minimal effort.

Role Variables
--------------

| Variable             | Default          | Meaning                                                                                |
|----------------------|------------------|----------------------------------------------------------------------------------------|
| postgresUser         | drupaluser       | Username used to specify the owner of the postgres database                            |
| postgresPassword     | drupal           | Password used to authenticate the postgresUser                                         |
| postgresDatabasename | drupal           | Name for the postgres database used for drupal                                         |
| postgresDatabaseDump | databasedump.sql | The database backup-file, used to provision the database (Place in /ansible directory) |
| drupalDirname        | corona2020.local | Name used to specify the drupal website (in /var/www/html). It is recommended to use your domain name |
| crtFile              | ca.crt           | The certificate used to enable the website with HTTPS                                  |
| keyFile              | ca.key           | The keyfile that goes along with the certificate                                       |
| enableHTTP           | true             | Allow traffic through HTTP                                                             |
| enableHTTPS          | true             | Allow traffic through HTTPS                                                            |

Dependencies
------------

None

Example Playbook
----------------

    - hosts: webservers
      roles:
         - { role: drupal_website_ansible, x: 42 }

License
-------

BSD
