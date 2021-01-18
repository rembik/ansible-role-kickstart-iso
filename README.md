Ansible Role: Kickstart ISO
===========================

[![][ci_badge]][ci]
[![][release_badge]][release]
[![][ansible_role_badge]][ansible_role]
[![][ansible_downloads_badge]][ansible_role]

This role creates kickstart ISO images for RHEL/CentOS.

Requirements
------------

- Access to repositories containing system packages and base ISO images, likely on the internet.
- A recent Ansible version (tested last 2 stable major versions).

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- rembik.bootstrap

```

Role Variables
--------------

These defaults are set in `defaults/main.yml`:

```yaml
---
# https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/anaconda_customization_guide/sect-boot-menu-customization
# https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/performing_an_advanced_rhel_installation

kickstart_iso_type: 'boot'
kickstart_iso_check_url: 'http://mirror.centos.org/centos/8/isos/x86_64/CHECKSUM.asc'
kickstart_iso_base_url: 'http://isoredirect.centos.org/centos/8/isos/x86_64/'
kickstart_iso_download_delay: 300

# Directory where the kickstart ISO images are created, if they do not already exist
kickstart_iso_storage: ".images/{{ kickstart_iso_info.file_name if kickstart_iso_info is defined else 'RHEL_CentOS' }}"

# Pick first disks with minimal physical size kickstart_iso_disk_drive_min_size (GiB)
# until a overall minimal logical OS volume size kickstart_iso_disk_volume_min_size (GiB)
# and create a logical OS volume with maximal size kickstart_iso_disk_volume_max_size (GiB)
kickstart_iso_disk_drive_min_size: 10
kickstart_iso_disk_volume_min_size: 60
kickstart_iso_disk_volume_max_size: 120

kickstart_iso_install_media: 'url --url http://mirror.centos.org/centos/8/BaseOS/x86_64/os/'
kickstart_iso_root_password: 'centos'
kickstart_iso_language: 'de'
kickstart_iso_country: 'DE'
kickstart_iso_timezone: 'Europe/Berlin'
kickstart_iso_completion: 'reboot'
kickstart_iso_network_bootproto: 'dhcp'
kickstart_iso_network_device: 'eth0'
kickstart_iso_network_static_netmask: '255.255.255.0'
kickstart_iso_network_static_gateway: '192.168.1.1'
kickstart_iso_network_static_nameserver: ['192.168.1.1']
# If kickstart_iso_network_bootproto is static use kickstart_iso_network_static_hosts
# to create additional custom static host ISO images
# kickstart_iso_network_static_hosts:
#   - {ip: '192.168.1.1', name: 'host01'}
```

Dependencies
------------

None.

Example Playbook
----------------

This is a sample playbook to create kickstart CentOS 8 ISO image on
localhost; made for network releases via DHCP.

```yaml
---
- hosts: localhost
  become: true

  tasks:
    - include_role:
        name: rembik.kickstart_iso
```

This is a sample playbook to create kickstart CentOS 7 ISO images on
localhost; made for static network configuration.

```yaml
---
- hosts: localhost
  become: true

  pre_tasks:
    - name: Get all hosts (including IP) from inventory
      set_fact:
        kickstart_iso_network_static_hosts: "{{ (kickstart_iso_network_static_hosts|default([])) +
                                             [dict(ip=hostvars[item].ansible_host,name=(item.split('.')[0]|lower))] }}"
      loop: "{{ groups['all'] }}"

  tasks:
    - include_role:
        name: rembik.kickstart_iso
      vars:
        kickstart_iso_type: 'Minimal'
        kickstart_iso_check_url: 'http://mirror.centos.org/centos/7/isos/x86_64/sha256sum.txt.asc'
        kickstart_iso_base_url: 'http://isoredirect.centos.org/centos/7/isos/x86_64/'
        kickstart_iso_install_media: 'cdrom'
        kickstart_iso_network_bootproto: 'static'
        kickstart_iso_network_static_netmask: '255.255.252.0'
        kickstart_iso_network_static_gateway: '10.0.0.1'
        kickstart_iso_network_static_nameserver:
          - '10.0.2.1'
          - '10.0.3.1'
```

Tests
-----

[![][python_badge]][python]
[![][ansible_badge]][ansible]

This role is tested periodically against the following Linux distributions:

|| [![][ansible_previous_badge]][ansible_previous] | [![][ansible_latest_badge]][ansible_latest] | [![][ansible_devel_badge]][ansible_devel] |
|---|---|---|---|
| [![][alpine_badge]][alpine] | [![][x]][ci] | [![][x]][ci] | [![][x]][ci] |
| [![][amazonlinux_badge]][amazonlinux] || [![][x]][ci] ||
| [![][centos_badge]][centos] | [![][x]][ci] | [![][x]][ci] | [![][x]][ci] |
| [![][debian_badge]][debian] | [![][x]][ci] | [![][x]][ci] | [![][x]][ci] |
| [![][fedora_badge]][fedora] | [![][x]][ci] | [![][x]][ci] | [![][x]][ci] |
| [![][opensuse_badge]][opensuse] | [![][x]][ci] | [![][x]][ci] | [![][x]][ci] |
| [![][redhat_badge]][redhat] | [![][x]][ci] | [![][x]][ci] | [![][x]][ci] |
| [![][ubuntu_badge]][ubuntu] | [![][x]][ci] | [![][x]][ci] | [![][x]][ci] |
| [![][alpine_preview_badge]][alpine] || [![][x]][ci] | [![][x]][ci] |
| [![][debian_preview_badge]][debian] || [![][x]][ci] | [![][x]][ci] |
| [![][fedora_preview_badge]][fedora] || [![][x]][ci] | [![][x]][ci] |
| [![][ubuntu_preview_badge]][ubuntu] || [![][x]][ci] | [![][x]][ci] |

> Asteriks means the build is allowed to fail, it's marked as an experimental build.

Contributing
------------

If you find issues, please register them at this [GitHub project issue page][issues] or consider contributing code by following this [guideline][contributing].

License
-------

[Apache License, Version 2.0][license]

Author Information
------------------

[Brian Rimek](https://github.com/rembik)


[ci]: https://github.com/rembik/ansible-role-kickstart-iso/actions?query=workflow%3ACI
[travis_ci]: https://travis-ci.org/github/rembik/ansible-role-kickstart-iso
[release]: https://github.com/rembik/ansible-role-kickstart-iso/releases
[ansible_role]: https://galaxy.ansible.com/rembik/kickstart_iso

[ci_badge]: https://img.shields.io/github/workflow/status/rembik/ansible-role-kickstart-iso/CI/master?logo=github&label=CI
[travis_ci_badge]: https://img.shields.io/travis/rembik/ansible-role-kickstart-iso/master.svg?logo=travis-ci&logoColor=EEE&label=CI
[release_badge]: https://img.shields.io/github/release/rembik/ansible-role-kickstart-iso.svg?sort=semver&colorB=56b4b6&logo=github&logoColor=EEE
[ansible_role_badge]: https://img.shields.io/ansible/role/36241.svg?colorB=56b4b6&logo=ansible&logoColor=EEE
[ansible_downloads_badge]: https://img.shields.io/ansible/role/d/36241.svg?label=downloads&logo=ansible&logoColor=EEE

[issues]: http://github.com/rembik/ansible-role-kickstart-iso/issues/new/choose
[contributing]: http://github.com/rembik/ansible-role-kickstart-iso/tree/master/.github/CONTRIBUTING.md
[license]: http://github.com/rembik/ansible-role-kickstart-iso/tree/master/LICENSE

[python]: https://www.python.org/
[ansible]: https://ansible.com/
[ansible_previous]: https://docs.ansible.com/ansible/2.9/
[ansible_latest]: https://docs.ansible.com/ansible/2.10/
[ansible_devel]: https://docs.ansible.com/ansible/devel/

[python_badge]: https://img.shields.io/badge/python-3.9-1488C6.svg
[ansible_badge]: https://img.shields.io/badge/Ansible-2.9%20%7C%202.10%20%7C%20devel%2A-56b4b6.svg
[ansible_previous_badge]: https://img.shields.io/badge/2.9-56b4b6.svg
[ansible_latest_badge]: https://img.shields.io/badge/2.10-56b4b6.svg
[ansible_devel_badge]: https://img.shields.io/badge/devel%2A-56b4b6.svg

[alpine]: https://hub.docker.com/_/alpine
[amazonlinux]: https://hub.docker.com/_/amazonlinux
[centos]: https://hub.docker.com/_/centos
[debian]: https://hub.docker.com/_/debian
[fedora]: https://hub.docker.com/_/fedora
[opensuse]: https://hub.docker.com/_/opensuse
[redhat]: https://access.redhat.com/containers/#/registry.access.redhat.com/ubi8/ubi
[ubuntu]: https://hub.docker.com/_/ubuntu

[alpine_badge]: https://img.shields.io/badge/Alpine-latest-1488C6.svg?logo=docker&logoColor=EEE
[alpine_preview_badge]: https://img.shields.io/badge/Alpine-edge%2A-1488C6.svg?logo=docker&logoColor=EEE
[amazonlinux_badge]: https://img.shields.io/badge/AmazonLinux-latest-1488C6.svg?logo=docker&logoColor=EEE
[centos_badge]: https://img.shields.io/badge/CentOS-latest-1488C6.svg?logo=docker&logoColor=EEE
[debian_badge]: https://img.shields.io/badge/Debian-latest-1488C6.svg?logo=docker&logoColor=EEE
[debian_preview_badge]: https://img.shields.io/badge/Debian-unstable%2A-1488C6.svg?logo=docker&logoColor=EEE
[fedora_badge]: https://img.shields.io/badge/Fedora-latest-1488C6.svg?logo=docker&logoColor=EEE
[fedora_preview_badge]: https://img.shields.io/badge/Fedora-rawhide%2A-1488C6.svg?logo=docker&logoColor=EEE
[opensuse_badge]: https://img.shields.io/badge/openSUSE-leap%20%7C%20tumbleweed-1488C6.svg?logo=docker&logoColor=EEE
[redhat_badge]: https://img.shields.io/badge/RedHat-latest-1488C6.svg?logo=docker&logoColor=EEE
[ubuntu_badge]: https://img.shields.io/badge/Ubuntu-latest-1488C6.svg?logo=docker&logoColor=EEE
[ubuntu_preview_badge]: https://img.shields.io/badge/Ubuntu-devel%2A-1488C6.svg?logo=docker&logoColor=EEE
[x]: https://img.shields.io/badge/X-grey.svg
