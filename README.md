Role Name
=========

ntp: Ntp

[![Build Status](https://travis-ci.org/cmihai-ansible/ntp.svg?branch=master)](https://travis-ci.org/cmihai-ansible/ntp)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.ntp](https://galaxy.ansible.com/devops-toolbox.ntp)

```bash
ansible-galaxy install devops-toolbox.ntp
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
ntp_packages_state: present
ntp_remove_packages: true
ntp_enable_service: true
ntp_enable_selinux: true
ntp_copy_templates: true
ntp_firewall_configure: true
ntp_firewall_rules:
  - service: ssh
  - port: 3389
ntp_users:
  - user: devops
    group: docker
ntp_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install ntp on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: ntp is configured
      import_role:
        name: devops-toolbox.ntp
      vars:
        ntp_packages_state: present
        ntp_remove_packages: true
        ntp_enable_service: true
        ntp_enable_selinux: true
        ntp_copy_templates: true
        ntp_firewall_configure: true
        ntp_firewall_rules:
          - service: ssh
          - port: 3389
        ntp_users:
          - user: devops
            group: docker
        ntp_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: ntp
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
