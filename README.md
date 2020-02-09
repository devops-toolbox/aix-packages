Role Name
=========

aix-packages: Aix-packages

[![Build Status](https://travis-ci.org/cmihai-ansible/aix-packages.svg?branch=master)](https://travis-ci.org/cmihai-ansible/aix-packages)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.aix-packages](https://galaxy.ansible.com/devops-toolbox.aix-packages)

```bash
ansible-galaxy install devops-toolbox.aix-packages
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
aix-packages_packages_state: present
aix-packages_remove_packages: true
aix-packages_enable_service: true
aix-packages_enable_selinux: true
aix-packages_copy_templates: true
aix-packages_firewall_configure: true
aix-packages_firewall_rules:
  - service: ssh
  - port: 3389
aix-packages_users:
  - user: devops
    group: docker
aix-packages_selinux_booleans:
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
- name: Install aix-packages on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: aix-packages is configured
      import_role:
        name: devops-toolbox.aix-packages
      vars:
        aix-packages_packages_state: present
        aix-packages_remove_packages: true
        aix-packages_enable_service: true
        aix-packages_enable_selinux: true
        aix-packages_copy_templates: true
        aix-packages_firewall_configure: true
        aix-packages_firewall_rules:
          - service: ssh
          - port: 3389
        aix-packages_users:
          - user: devops
            group: docker
        aix-packages_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: aix-packages
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
