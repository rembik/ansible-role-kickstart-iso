Ansible Role: Kickstart ISO
===========================

[![Build Status](https://img.shields.io/travis/rembik/ansible-role-kickstart-iso/master.svg?style=popout-square&logo=travis&logoColor=444&colorA=aaa)](https://travis-ci.org/rembik/ansible-role-kickstart-iso)
[![GitHub release](https://img.shields.io/github/release/rembik/ansible-role-kickstart-iso.svg?style=popout-square&logo=github&logoColor=444&colorA=aaa)](https://github.com/rembik/ansible-role-kickstart-iso/releases)
[![Ansible Role](https://img.shields.io/ansible/role/36241.svg?style=popout-square&logo=data:image/png;base64,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&logoColor=444&colorA=aaa)](https://galaxy.ansible.com/rembik/kickstart_iso)
[![Ansible Role downloads](https://img.shields.io/ansible/role/d/36241.svg?style=popout-square&logo=data:image/png;base64,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&logoColor=444&colorA=aaa)](https://galaxy.ansible.com/rembik/kickstart_iso)

This role creates custom kickstart ISO images for:
* RHEL 7
* CentOS 7

Requirements
------------

None.

Role Variables
--------------

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/anaconda_customization_guide/sect-boot-menu-customization

image_name: 'CentOS 7 x86_64'
image_type: 'Minimal'
image_check_url: 'http://mirror.centos.org/centos/7/isos/x86_64/sha256sum.txt.asc'
image_base_url: 'http://isoredirect.centos.org/centos/7/isos/x86_64/'

image_src_dir: ".images/{{ image_name|replace(' ','-') }}"
image_dest_dir: ".images/{{ image_name|replace(' ','-') }}"

image_bios_conf_file: 'isolinux/isolinux.cfg'
image_uefi_conf_file: 'EFI/BOOT/grub.cfg'
image_boot_name: "{{ image_name|replace(' ','\\x20') }}"

# Pick first disks with minimal physical size image_disk_drive_min_size (GiB)
# until a overall minimal logical OS volume size image_disk_volume_min_size (GiB)
# and create a logical OS volume with maximal size image_disk_volume_max_size (GiB)
image_disk_drive_min_size: 10
image_disk_volume_min_size: 60
image_disk_volume_max_size: 120

image_root_password: 'centos'
image_language: 'de'
image_country: 'DE'
image_timezone: 'Europe/Berlin'
image_network_bootproto: 'dhcp'
image_network_device: 'eth0'
image_network_static_netmask: '255.255.255.0'
image_network_static_gateway: '192.168.1.1'
image_network_static_nameserver: ['192.168.1.1']
# If image_network_bootproto is static use image_network_static_hosts
# to create custom static host ISO images
# image_network_static_hosts:
#   - {ip: '192.168.1.1', name: 'host01'}
```

Dependencies
------------

None.

Example Playbook
----------------

This is a sample playbook file for the Ansible role to create an kickstart CentOS 7 ISO image on
localhost; made for network releases via DHCP.

```yaml
---
- hosts: localhost
  become: true

  roles:
    - role: rembik.kickstart_iso
```

This is a sample playbook file for the Ansible role to create kickstart CentOS 7 ISO images on
localhost with custom variables; made for static network configuration.

```yaml
---
- hosts: localhost
  become: true

  pre_tasks:
    - name: Get all hosts (including IP) from inventory
      set_fact:
        image_network_static_hosts: "{{ (image_network_static_hosts|default([])) +
                                     [dict(ip=hostvars[item].ansible_host, name=(item.split('.')[0]|lower))] }}"
      loop: "{{ groups['all'] }}"

  roles:
    - role: rembik.kickstart_iso
      vars:
        image_network_bootproto: 'static'
        image_network_static_netmask: '255.255.252.0'
        image_network_static_gateway: '10.0.0.1'
        image_network_static_nameserver:
          - '10.0.2.1'
          - '10.0.3.1'
```

To run any of the above sample playbooks create a `playbook.yml` file and paste the contents.
Executing the Ansible Playbook is then as simple as executing `ansible-playbook playbook.yml`.

License
-------

[Apache License, Version 2.0](https://github.com/rembik/ansible-role-kickstart-iso/blob/master/LICENSE)

Author Information
------------------

This role was created in 2019 by Brian Rimek.
