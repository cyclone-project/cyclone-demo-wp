CYCLONE Federated Identity Wordpress Demo for Local Installation 
=========================================
This repository is a trimmed version of the [Wordpress in Docker Demo] (https://github.com/cyclone-project/cyclone-demo-wp-docker).

It is intended for a manual installation of Wordpress with [The Generic OpenID Connect Plugin](https://wordpress.org/plugins/generic-openid-connect/)  installed. 

For the deployment, the cloud application user copies the WP files to the server and adds the necessary tables
to the MySQL database by restoring the MySQL dump (cyclone_wp_openid.sql)

To integrate with the CYCLONE Federation Provider, the configuration looks like this:

```
mysql> SELECT * FROM wp_options WHERE option_name LIKE 'gen_openid_con%';
+-----------+------------------------------+-------------------------------------------------------------------------------------------+----------+
| option_id | option_name                  | option_value                                                                              | autoload |
+-----------+------------------------------+-------------------------------------------------------------------------------------------+----------+
|       172 | gen_openid_con_allowed_regex | ([A-Za-z0-9\-\_]+)                                                                        | yes      |
|       168 | gen_openid_con_client_id     | test                                                                                      | yes      |
|       169 | gen_openid_con_client_secret |                                                                                           | yes      |
|       164 | gen_openid_con_ep_login      | https://federation.cyclone-project.eu/auth/realms/master/protocol/openid-connect/auth     | yes      |
|       165 | gen_openid_con_ep_token      | https://federation.cyclone-project.eu/auth/realms/master/protocol/openid-connect/token    | yes      |
|       166 | gen_openid_con_ep_userinfo   | https://federation.cyclone-project.eu/auth/realms/master/protocol/openid-connect/userinfo | yes      |
|       171 | gen_openid_con_identity_key  | sub                                                                                       | yes      |
|       167 | gen_openid_con_no_sslverify  | 1                                                                                         | yes      |
|       170 | gen_openid_con_scope         | openid                                                                                    | yes      |
|       163 | gen_openid_con_use_autologin | 1                                                                                         | yes      |
+-----------+------------------------------+-------------------------------------------------------------------------------------------+----------+
```



