openldap
========

Installs and configures OpenLDAP

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

| Name                                   | Default                                                                                             | Description |
|----------------------------------------|-----------------------------------------------------------------------------------------------------|-------------|
| openldap_domain                        | example.com                                                                                         |             |
| openldap_organization                  | example                                                                                             |             |
| openldap_admin_password                | password                                                                                            |             |
| openldap_default_services              | ldap:/// ldapi:///                                                                                  |             |
| openldap_default_options               | ""                                                                                                  |             |
| openldap_server_schemas                | ['core', 'cosine', 'inetorgperson']                                                                 |             |
| openldap_server_loglevel               | none                                                                                                |             |
| openldap_server_modules                | ['back_hdb', 'syncprov']                                                                            |             |
| openldap_server_database               | hdb                                                                                                 |             |
| openldap_server_suffix                 | dc=example,dc=com                                                                                   |             |
| openldap_server_rootdn                 | cn=Manager,dc=example,dc=com                                                                        |             |
| openldap_server_rootpw                 | password                                                                                            |             |
| openldap_server_indexes                | ['objectClass,cn eq', 'entryCSN,entryUUID eq']                                                      |             |
| openldap_server_acls                   | ['to attrs=userPassword by anonymous auth by self write by * none', 'to * by self write by * none'] |             |
| openldap_server_password_hash          | "{SSHA}"                                                                                            |             |
| openldap_dbconfig_set_cachesize        | 2097152                                                                                             |             |
| openldap_dbconfig_set_lk_max_objects   | 1500                                                                                                |             |
| openldap_dbconfig_set_lk_max_locks     | 1500                                                                                                |             |
| openldap_dbconfig_set_lk_max_lockers   | 1500                                                                                                |             |
| openldap_client_uri                    | ldap://localhost                                                                                    |             |
| openldap_client_base                   | dc=example,dc=com                                                                                   |             |
| openldap_client_binddn                 | cn=Manager,dc=example,dc=com                                                                        |             |
| openldap_client_sizelimit              | 0                                                                                                   |             |
| openldap_client_timelimit              | 0                                                                                                   |             |
| openldap_sync_syncprov_checkpoint      | 50 10                                                                                               |             |
| openldap_sync_syncprov_sessionlog      | 100                                                                                                 |             |
| openldap_sync_consumer                 | false                                                                                               |             |
| openldap_sync_syncrepl_rid             | 001                                                                                                 |             |
| openldap_sync_syncrepl_provider        | ldap://ldap.example.com                                                                             |             |
| openldap_sync_syncrepl_type            | refreshAndPersist                                                                                   |             |
| openldap_sync_syncrepl_interval        | 00:00:05:00                                                                                         |             |
| openldap_sync_syncrepl_searchbase      | "{{ openldap_server_suffix}}"                                                                       |             |
| openldap_sync_syncrepl_binddn          | cn=admin,dc=example,dc=com                                                                          |             |
| openldap_sync_syncrepl_credentials     | secret                                                                                              |             |
| openldap_sync_syncrepl_starttls        | "no"                                                                                                |             |
| openldap_sync_syncrepl_retry           | 60 +                                                                                                |             |
| openldap_sync_syncrepl_bindmethod      | simple                                                                                              |             |
| openldap_sync_syncrepl_timeout         | 0                                                                                                   |             |
| openldap_sync_syncrepl_network_timeout | 0                                                                                                   |             |
| openldap_sync_syncrepl_keepalive       | 0:0:0                                                                                               |             |
| openldap_sync_syncrepl_filter          | (objectclass=\u002a)                                                                                |             |
| openldap_sync_syncrepl_scope           | sub                                                                                                 |             |
| openldap_sync_syncrepl_schemachecking  | off                                                                                                 |             |

Dependencies
------------

None

Example Playbook
----------------

Install OpenLDAP
```
- hosts: all
  roles:
    - { role: kbrebanov.openldap }
```

Install OpenLDAP specifying domain, organization and admin password
```
- hosts: all
  roles:
    - { role: kbrebanov.openldap, openldap_domain: 'site.com', openldap_organization: 'site', opendlap_admin_password: 'supersecret' }
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
