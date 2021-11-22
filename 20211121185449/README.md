# Managing server in public

With GitHub actions, servers can be managed with two repositories: one public with configurations and one private with connection information.

## Public configuration

Ansible configuration file are hosted here. Configurations can be separated by logic (`server`, `webserver`, `container`) or with an hash, so specific servers are obfuscated. No private information should be store here, not even user name. Maybe use hash that'll be converted when applying the config.

## Private configuration

Series of Ansible hosts file with connection informations. Public hashes can be stored with each server if needed. Contain also information for Github Actions.

## GH Actions

A GH action can be triggered when public or private repo is modified. Secrets are loaded from private repository from configuration files or environment variables.

