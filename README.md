Teleport Ansible Role
=====================

[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-hanxhx.teleport-blue.svg)](https://galaxy.ansible.com/hanxhx/teleport/) [![Build Status](https://app.travis-ci.com/HanXHX/ansible-teleport.svg?branch=master)](https://app.travis-ci.com/HanXHX/ansible-teleport)

Install and configure Teleport on Debian based OS

Requirements
------------

Due to packaging limitations, this role needs systemd.

Role Variables
--------------

...

Dependencies
------------

None.

Example Playbook
----------------

Simple full node:

```
- hosts: full.node.tld
  vars:
    teleport_config_auth_service_tokens:
      - 'node:my_super_TOKEN'
  roles:
    - hanxhx.teleport
```

SSH node:

```
- hosts: ssh.node.tld
  vars:
    teleport_config_teleport_auth_token: 'my_super_TOKEN'
    teleport_config_teleport_auth_servers: ['full.node.tld:443']
    teleport_config_auth_service_enabled: 'no'
    teleport_config_proxy_service_enabled: 'no'
  roles:
    - hanxhx.teleport
```

License
-------

GPLv2

Donation
--------

If this code helped you, or if you’ve used them for your projects, feel free to buy me some :beers:

- Bitcoin: `1BQwhBeszzWbUTyK4aUyq3SRg7rBSHcEQn`
- Ethereum: `63abe6b2648fd892816d87a31e3d9d4365a737b5`
- Litecoin: `LeNDw34zQLX84VvhCGADNvHMEgb5QyFXyD`
- Monero: `45wbf7VdQAZS5EWUrPhen7Wo4hy7Pa7c7ZBdaWQSRowtd3CZ5vpVw5nTPphTuqVQrnYZC72FXDYyfP31uJmfSQ6qRXFy3bQ`

No crypto-currency? :star: the project is also a way of saying thank you! :sunglasses:

Author Information
------------------

- Twitter: [@hanxhx_](https://twitter.com/hanxhx_)
