[![Build Status](https://travis-ci.org/zaxos/swapfile-ansible-role.svg?branch=master)](https://travis-ci.org/zaxos/swapfile-ansible-role)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-_zaxos.swapfile--ansible--role-blue.svg)](https://galaxy.ansible.com/zaxos/swapfile-ansible-role/)

swapfile-ansible-role
====================

Ansible role to configure swap file.

Requirements
------------
* centos/rhel 7
* ansible >= 1.8

Installation
------------
```
$ ansible-galaxy install zaxos.swapfile-ansible-role
```

Example Playbook
----------------
```yaml
- hosts: servers
  vars:
    swapfile_size_mb: 2048
  roles:
    - role: zaxos.swapfile-ansible-role
```

Role Variables
--------------
The main variable:
- `swapfile_size_mb`: Swap file size in MB. Default value is set equal to total physical memory (ansible_memtotal_mb).

Some variables that require review:
- `swapfile_state`: Default value is "present". Change to "absent" to remove swap file. 
- `swapfile_path`: Path in which swap file will be stored. Default is "/swap".
- `swapfile_filename`: Swap file name. Default is "swapfile".

Optional variables:
- `swapfile_swappiness`:  Sets "vm.swappiness" percentage value. This parameter controls the relative weight given to swapping out runtime memory, as opposed to dropping pages from the system page cache. Increasing the value increases the amount of swapping.
- `swapfile_vfs_cache_pressure`: Sets "vm.vfs_cache_pressure" value. This parameter controls the tendency of the kernel to reclaim the memory which is used for caching of VFS caches, versus pagecache and swap. Increasing this value increases the rate at which VFS caches are reclaimed.
