postfix [![Build Status](https://travis-ci.org/holms/ansible-postfix.svg?branch=master)](https://travis-ci.org/holms/ansible-postfix)
====

Postfix and Dovecot SASL with system user role.

Forked from holms/ansible-postfix

Currently only outgoing emails supported

Requirements
------------

Ansible version 2.7.8

## Platforms

* Ubuntu 18.04

Role Variables
--------------

Variable name | Variable value |
--------------|-----------------
postfix_domain| example.com
postfix_full_domain| my.example.com
postfix_local_domain | mx
postfix_users | { name: myuser, password: _sha512_password_hash }

Example
-------

playbook.yml:
```
- name: install newsletter servers
  hosts: newsletterserver
  user: root
  roles:
    - postfix-sasl-dovecot
```

hosts:
```
[newsletterserver]
newsletter.example.com
```

host_vars/newsletter.example.com.yml
```
postfix_full_domain: newsletter.example.com
postfix_domain: newsletter.example.com
postfix_local_domain: newsletter
postfix_users:
  newsletter:
    password: "my_secret_password"
    mysecretsalt: "some_salt_shorter_than_16_chars_without_special_chars"
```

License
-------

MIT

Author Information
------------------

Alexander Rusa (<alex@rusa.at>)

based on project by:
Roman Gorodeckij (<holms@holms.lt>)
