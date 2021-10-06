## Note about this folder

Inside this directory the credentials.yml protected by ansible-vault is expected. The content of that file should include:
```
vault_mysql_root_passwords:
  ns1: Root password of the MariaDB/MySQL instance in ns1 host
  nsX: 
vault_pdns_api_key: PDNS API key
vault_mysql_pdns_user_password: Password of the DB user for PDNS
vault_mysql_replication_user_password: MariaDB/MySQL replication user password
```