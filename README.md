libvirt
=========

Install and configure libvirt on Fedora.

Requirements
------------

Your computer must have enough hardware resources to support running
virtual machines. You might also have to enable virtualization in your
computer's BIOS.

Role Variables
--------------

|name|description|type|default|
|---|---|---|---|
|libvirt_pool_name|Default pool's name|string|default|
|libvirt_pool_dir|Path to default pool directory|directory path|"{{ ansible_user_dir }}/VirtualMachines"|


Example Playbook
----------------

```yaml
- hosts: workstations
  tasks:
  - import_role:
      name: libvirt
    vars:
      libvirt_pool_name: default
      libvirt_pool_dir: "{{ ansible_user_dir }}/VirtualMachines"
```

License
-------

[MIT](LICENSE)
