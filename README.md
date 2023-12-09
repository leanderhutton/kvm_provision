kvm_provision Role
=========

Deployes libvirt virtual machines from various template sources.


Requirements
------------

Community libvirt:

```
ansible-galaxy collection install community.libvirt
```

Example Playbook
----------------

```
- name: Deploys VM based on template image
  hosts: localhost
  gather_facts: yes
  become: yes
  vars:
    pool_dir: "/var/lib/libvirt/images"
    vm: debian_12
    vcpus: 2
    ram_mb: 2048
    cleanup: no
    vm_user: beegyoshi
    vm_pass: stinky
    net: bridged-network

  tasks:
    - name: KVM Provision role
      include_role:
        name: kvm_provision
      vars:
        libvirt_pool_dir: "{{ pool_dir }}"
        vm_name: "{{ vm }}"
        vm_vcpus: "{{ vcpus }}"
        vm_ram_mb: "{{ ram_mb }}"
        vm_net: "{{ net }}"
        cleanup_tmp: "{{ cleanup }}"

```
Author Information
------------------

leander@one-button.org
