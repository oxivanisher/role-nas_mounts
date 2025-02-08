nas_mounts
==========
[![Ansible Lint](https://github.com/oxivanisher/role-nas_mounts/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/oxivanisher/role-nas_mounts/actions/workflows/ansible-lint.yml)

Mount filesystems from a NAS. Currently only cifs is supported.

For cifs, the file `/etc/cifspw` will be configured wih the supplied username and password. The file will be only readable by root.

Role Variables
--------------

| Name          | Comment                              | Default value |
|---------------|--------------------------------------|---------------|
| nas_mounts_os_user  | The user on the system for which the mounts are configured  |           |
| nas_mounts_cifs_user | The CIFS username on the nas |          |
| nas_mounts_cifs_password | The CIFS password on the nas |          |
| nas_mounts_cifs_mounts | A list of dicts containing `src` and `dest`. | `[]`     |

Example config:
```yaml
nas_mounts_os_user: pi
nas_mounts_cifs_user: usera
nas_mounts_cifs_password: passwordb
nas_mounts_cifs_mounts:
  - src: //10.0.100.3/my-files
    dest: /mnt/nas/my-files
  - src: //10.0.100.4/more-files
    dest: /mnt/nas/more-files
```

Example Playbook
----------------
```yaml
- name: Mount NAS drives
  hosts: client
  collections:
    - oxivanisher.linux_desktop
  roles:
    - role: oxivanisher.linux_desktop.nas_mounts
```

License
-------

BSD

Author Information
------------------

This role is part of the [oxivanisher.linux_desktop](https://galaxy.ansible.com/ui/repo/published/oxivanisher/linux_desktop/) collection, and the source for that is located on [github](https://github.com/oxivanisher/collection-linux_desktop).
