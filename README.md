# Ansible Role: Logrotate

[![Build Status](https://api.travis-ci.com/agmalpartida/ansible-role-logrotate.svg?branch=master)](https://travis-ci.com/github/agmalpartida/ansible-role-logrotate)

This role will deal with the setup of __Logrotate__.

Requirements
------------

-

Role Variables
--------------

-

Dependencies
------------

-

Example Playbook
----------------

### Configuration example

```yaml
logfile:
  one:
    name:      "example1"
    path:      "/var/log/example1.log"
    compress:  "compress"
    notify:    "notifempty"
    missing:   "missingok"
    size:      "size 10k"
    daily:     "daily"
    owner:     "create 0644 root root"
  two:
    name:      "example2"
    path:      "/var/log/example2.log"
    compress:  "compress"
    notify:    "notifempty"
    missing:   "missingok"
    size:      "size 10k"
    daily:     "daily"
    owner:     "create 0644 root root"
```

### Example playbook

```yaml
- hosts: all
  gather_facts: true
  become: yes

  pre_tasks:
    - include_vars: "{{ item }}"
      with_items:
        - "../host_vars/{{ ansible_hostname }}.yml"
        - "../group_vars/linux.yml"
      tags:
        node_check

  roles:
    - role: logrotate
```

License
-------

BSD

Author Information
------------------

agmalpartida
