#### Ansible systemd_service

This Ansible role that installs and configures systemd unit files and all of its
corresponding services. This role requires the ``openstack-ansible-plugins``
repository to be available on your local system. The Ansible galaxy resolver
will not retrieve this role for you. To get this role in place clone the
plugins repository **before** installing this role.

``` bash
# git clone https://github.com/openstack/openstack-ansible-plugins /etc/ansible/roles/plugins
```

You can also use the ``ansible-galaxy`` command on the ``ansible-role-requirements.yml`` file.

``` bash
# ansible-galaxy install -r ansible-role-requirements.yml
```

----

###### Example playbook

``` yaml
- name: Create a systemd unit file for ServiceX
  hosts: localhost
  become: true
  roles:
    - role: "systemd_service"
      systemd_services:
        - service_name: ServiceX
          execstarts:
            - /path/ServiceX --flag1
      tags:
        - servicex-init

```
