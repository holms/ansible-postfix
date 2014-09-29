postfix [![Build Status](https://travis-ci.org/holms/ansible-postfix.svg?branch=master)](https://travis-ci.org/holms/ansible-postfix)
====

Postfix and Dovecot SASL with system user role.

Currently only outgoing emails supported

Requirements
------------

Ansible version 1.6

## Platforms

* Ubuntu 14.10

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

```
- hosts: my.example.com:my
  user: root

  vars:

    postfix_full_domain: my.example.com
    postfix_domain: example.com
    postfix_local_domain: my
    postfix_users:
        - { name: whatever, password: _sha512_hash_here }  # use mkpasswd tool to generate one

  roles:
    - { role: postfix }
```

License
-------

MIT

Author Information
------------------

Roman Gorodeckij (<holms@holms.lt>)
