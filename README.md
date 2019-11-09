Ansible Role: Kickstart ISO
===========================

[![Build Status](https://img.shields.io/travis/rembik/ansible-role-kickstart-iso/master.svg?logo=travis-ci&logoColor=EEE)][travis_ci]
[![GitHub release](https://img.shields.io/github/release/rembik/ansible-role-kickstart-iso.svg?&colorB=56b4b6&logo=github&logoColor=EEE)](https://github.com/rembik/ansible-role-kickstart-iso/releases)
[![Ansible Role](https://img.shields.io/ansible/role/36241.svg?colorB=56b4b6&logo=ansible&logoColor=EEE)][ansible_galaxy]
[![Ansible Role downloads](https://img.shields.io/ansible/role/d/36241.svg?label=downloads&logo=ansible&logoColor=EEE)][ansible_galaxy]

This role creates kickstart ISO images for RHEL/CentOS.

Requirements
------------

- Access to repositories containing system packages and base ISO images, likely on the internet.
- A recent Ansible version (tested last 3 major versions).

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

kickstart_iso_name: 'CentOS 8 x86_64'
kickstart_iso_type: 'boot'
kickstart_iso_check_url: 'http://mirror.centos.org/centos/8/isos/x86_64/CHECKSUM.asc'
kickstart_iso_base_url: 'http://isoredirect.centos.org/centos/8/isos/x86_64/'
kickstart_iso_download_delay: 300

# Directory where the kickstart ISO images are created, if they do not already exist
kickstart_iso_storage: ".images/{{ kickstart_iso_name|replace(' ','-') }}"

# Pick first disks with minimal physical size kickstart_iso_disk_drive_min_size (GiB)
# until a overall minimal logical OS volume size kickstart_iso_disk_volume_min_size (GiB)
# and create a logical OS volume with maximal size kickstart_iso_disk_volume_max_size (GiB)
kickstart_iso_disk_drive_min_size: 10
kickstart_iso_disk_volume_min_size: 60
kickstart_iso_disk_volume_max_size: 120

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

  roles:
    - role: rembik.kickstart_iso
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

  roles:
    - role: rembik.kickstart_iso
      vars:
        kickstart_iso_name: 'CentOS 7 x86_64'
        kickstart_iso_type: 'Minimal'
        kickstart_iso_check_url: 'http://mirror.centos.org/centos/7/isos/x86_64/sha256sum.txt.asc'
        kickstart_iso_base_url: 'http://isoredirect.centos.org/centos/7/isos/x86_64/'
        kickstart_iso_network_bootproto: 'static'
        kickstart_iso_network_static_netmask: '255.255.252.0'
        kickstart_iso_network_static_gateway: '10.0.0.1'
        kickstart_iso_network_static_nameserver:
          - '10.0.2.1'
          - '10.0.3.1'
```

Role Tests
----------

[![Python](https://img.shields.io/badge/python-3.7-1488C6.svg)](https://www.python.org/)
[![Ansible](https://img.shields.io/badge/Ansible-2.7%20%7C%202.8%20%7C%202.9%20%7C%20devel%2A-56b4b6.svg)](https://ansible.com/)

This role is tested periodically against the following Linux distributions:

|| [![Ansible](https://img.shields.io/badge/2.7-56b4b6.svg)](https://docs.ansible.com/ansible/2.7/) | [![Ansible](https://img.shields.io/badge/2.8-56b4b6.svg)](https://docs.ansible.com/ansible/2.8/) | [![Ansible](https://img.shields.io/badge/2.9-56b4b6.svg)](https://docs.ansible.com/ansible/2.9/)| [![Ansible](https://img.shields.io/badge/devel%2A-56b4b6.svg)](https://docs.ansible.com/ansible/devel/) |
|---|---|---|---|---|
| [![DockerDistro](https://img.shields.io/badge/Alpine-latest%20%7C%20edge%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/alpine) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/AmazonLinux-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/amazonlinux) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/CentOS-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/centos) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/Debian-latest%20%7C%20unstable%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/debian) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/Fedora-latest%20%7C%20rawhide%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/fedora) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/openSUSE-Leap%20%7C%20Tumbleweed-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/opensuse) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/RedHat-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://access.redhat.com/containers/#/registry.access.redhat.com/ubi8/ubi) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/Ubuntu-latest%20%7C%20devel%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/ubuntu) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |

> Asteriks means the build is allowed to fail, it's marked as an experimental build.

Contributing
------------

If you find issues, please register them at this [GitHub project issue page](https://github.com/rembik/ansible-role-kickstart-iso/issues/new/choose) or consider contributing code by following this [guideline](http://github.com/rembik/ansible-role-kickstart-iso/tree/master/.github/CONTRIBUTING.md).

License
-------

[Apache License, Version 2.0](https://github.com/rembik/ansible-role-kickstart-iso/blob/master/LICENSE)

Author Information
------------------

[Brian Rimek](https://github.com/rembik)

[travis_ci]: https://travis-ci.org/rembik/ansible-role-kickstart-iso
[ansible_galaxy]: https://galaxy.ansible.com/rembik/kickstart_iso
