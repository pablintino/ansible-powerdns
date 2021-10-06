# Ansible Playbook for PowerDNS install

## Description
This playbook installs and configures PowerDNS Authoritative and PowerDNS Recursor servers in a set of machines based on the Ansible inventory.
PowerDNS Authoritative servers are configured to use a replicating MySQL/MariaDB database that makes zones replication transparent.

## Behavior
The playbook configures PowerDNS recursor to be listening on the standard DNS port 53. The recursor will forward all request to the configured forwarders (this repo uses Google ones), except the ones whose zones matches a particular pattern. That zones will be redirected to the local authoritative server that is listening on port 5300.
All this configuration can be changed by modifying the *pdns_rec_config.forward-zones* list in [inventory/group_vars/all.yml](inventory/group_vars/all.yml).

## Requirements
- Ansible >  2.10
- At least one target machine for the master DNS node

## Security notes
- All the used credentials are stored in the ansible-vault protected [data/credentials/credentials.yml](data/credentials/credentials.yml) file. Check the structure 
that this file should contain by reviewing the [Readme](data/credentials/README.md)
- This playbook doesn't apply any security measure and/or restrictions.

