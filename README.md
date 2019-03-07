Ansible Role: Kickstart ISO
===========================

[![Build Status](https://img.shields.io/travis/rembik/ansible-role-kickstart-iso/master.svg?logo=travis&logoColor=EEE)](https://travis-ci.org/rembik/ansible-role-kickstart-iso)
[![GitHub release](https://img.shields.io/github/release/rembik/ansible-role-kickstart-iso.svg?&colorB=56b4b6&logo=github&logoColor=EEE)](https://github.com/rembik/ansible-role-kickstart-iso/releases)
[![Ansible Role](https://img.shields.io/ansible/role/36241.svg?colorB=56b4b6&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAEdUlEQVRYR61Xa4iUVRh+n8PMCjXOzHlPmZUlZlgpoVBBUdBlUyExTRJsyUrqdxcw6EKhBEUX6fKvG5l0IUvZUKSr1I8uZpCUCVLE0lZo6znn29mVcpv53jjTzDLOzux3Vvv+fs/znOf7zvO+7zmgE3hE5NQkSU4HcBoAJSJHSqXSEICRqcohllCpVObVarVb0jTtAzCvE09EDgPYLSKfAniPmYez9DMNeO+vTdP0QQCLs8Ta3h8hoke01i8BSLtxuxpwzpVEZDuA66a4cDv8u56enhsKhcKhTjodDXjvZ6dp+iGAC05y8TpdRH4noqXGmB/b9SYYsNbOIqJvAZzxfyze1BCRChFdYYw50Kp7nIGQbufcXgAXRS5eI6JfiWhOJH4wn89fMn369KEm/jgD1tqtAFZHihGAdeVyeYtz7msAl0XyvmDmqyYYSJLk0jRN90aKhH09xMxnh4Rba1cD2BrLJaJbmfnNgB//A9bajwFcHysC4FGt9WONkOWcc4MAZsbwReQPZj4PwLG6Ae/9QhHZF0NuYKq5XG5msVi03vs7tNabrbUbg6kpaNT/Qt2Ac+4JInpgCuS3mbnPe3+NiLzGzHNGR0dnjo2NhXJTkTrvMPOapoGQ5HMiiWH/rzTGfGmt3QzgdgA3aa37rbXbAKyK1BnWWht478si4iNJYfEDxpgFbbz3mXllkiS9aZp+EquVy+UuhLV2AYD9sSQRucsY86r3/l4ReXa8nIA5WusB59xPRHR+jJ5SqhdJkixO0/SjGELoZsw8I6TXe79SRDYTUalRCRuNMRu89/eIyHMxekS0NhhYEvp+DAHAJq31+ibWe7+oYWIhEQ2EMFpriwD+JKJpWZr1/DjnLiai77PA/80UmW2MGXTOvaCU6i+Xy7sbWQh/YkUzjN77l8NWZWkqpZaiUqmYarUaZnfWs4uZlzXwodzyYd4z8+OBaK3dAGBRCGNsrgK+WYa/RAyUZcy8yzl3PxE91eJ2p9Z6DYCjoS8Q0T6tdWKt/QrA5ZN81ZjWmusGrLXPA7h7EvCg1np2o2sOENG5rVgROZjP51cUi8WDLflYKyJbJtHcwcw31g1kVYKIrDfGbLLWLgXwQSdRETmqlLpNa729URXTvPdhq0wnPIDQwl+vGxCREMb9AOZ3AB8TkRnGmIpzrj+ELSMsT2qtH2pMyVcA3NkBb7XWswD8PT4NvfdXi8hnHcA/i0gYnQrAw5G9fgeA7SKyiYi4XRPAfVrreq9oP5C8C+DmrHI4mfci8hszzwUwNsGAiBScc3u6bMXJrFvnishfoTKYebzvdDqUhqn4TezhYoquljPzzlZO12N5uN0Q0dwpLtAN/g8RrWsewzINBMDw8DDXarVtRBSaywk/IjKilFqutf68YzlmKTvn+kTkGQBnZmFb34vIqFLqxXw+/3ShUDjcjZt5N2yE5xTv/SoR6SWiJQDO6iYoInuUUm8ppd4olUouy3SUgXaRkZGRGdVqdb6IhAtMGL9DIhKu5z+EQ0nWoq3v/wWf4hm52dSUyAAAAABJRU5ErkJggg==)](https://galaxy.ansible.com/rembik/kickstart_iso)
[![Ansible Role downloads](https://img.shields.io/ansible/role/d/36241.svg?label=downloads&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAEdUlEQVRYR61Xa4iUVRh+n8PMCjXOzHlPmZUlZlgpoVBBUdBlUyExTRJsyUrqdxcw6EKhBEUX6fKvG5l0IUvZUKSr1I8uZpCUCVLE0lZo6znn29mVcpv53jjTzDLOzux3Vvv+fs/znOf7zvO+7zmgE3hE5NQkSU4HcBoAJSJHSqXSEICRqcohllCpVObVarVb0jTtAzCvE09EDgPYLSKfAniPmYez9DMNeO+vTdP0QQCLs8Ta3h8hoke01i8BSLtxuxpwzpVEZDuA66a4cDv8u56enhsKhcKhTjodDXjvZ6dp+iGAC05y8TpdRH4noqXGmB/b9SYYsNbOIqJvAZzxfyze1BCRChFdYYw50Kp7nIGQbufcXgAXRS5eI6JfiWhOJH4wn89fMn369KEm/jgD1tqtAFZHihGAdeVyeYtz7msAl0XyvmDmqyYYSJLk0jRN90aKhH09xMxnh4Rba1cD2BrLJaJbmfnNgB//A9bajwFcHysC4FGt9WONkOWcc4MAZsbwReQPZj4PwLG6Ae/9QhHZF0NuYKq5XG5msVi03vs7tNabrbUbg6kpaNT/Qt2Ac+4JInpgCuS3mbnPe3+NiLzGzHNGR0dnjo2NhXJTkTrvMPOapoGQ5HMiiWH/rzTGfGmt3QzgdgA3aa37rbXbAKyK1BnWWht478si4iNJYfEDxpgFbbz3mXllkiS9aZp+EquVy+UuhLV2AYD9sSQRucsY86r3/l4ReXa8nIA5WusB59xPRHR+jJ5SqhdJkixO0/SjGELoZsw8I6TXe79SRDYTUalRCRuNMRu89/eIyHMxekS0NhhYEvp+DAHAJq31+ibWe7+oYWIhEQ2EMFpriwD+JKJpWZr1/DjnLiai77PA/80UmW2MGXTOvaCU6i+Xy7sbWQh/YkUzjN77l8NWZWkqpZaiUqmYarUaZnfWs4uZlzXwodzyYd4z8+OBaK3dAGBRCGNsrgK+WYa/RAyUZcy8yzl3PxE91eJ2p9Z6DYCjoS8Q0T6tdWKt/QrA5ZN81ZjWmusGrLXPA7h7EvCg1np2o2sOENG5rVgROZjP51cUi8WDLflYKyJbJtHcwcw31g1kVYKIrDfGbLLWLgXwQSdRETmqlLpNa729URXTvPdhq0wnPIDQwl+vGxCREMb9AOZ3AB8TkRnGmIpzrj+ELSMsT2qtH2pMyVcA3NkBb7XWswD8PT4NvfdXi8hnHcA/i0gYnQrAw5G9fgeA7SKyiYi4XRPAfVrreq9oP5C8C+DmrHI4mfci8hszzwUwNsGAiBScc3u6bMXJrFvnishfoTKYebzvdDqUhqn4TezhYoquljPzzlZO12N5uN0Q0dwpLtAN/g8RrWsewzINBMDw8DDXarVtRBSaywk/IjKilFqutf68YzlmKTvn+kTkGQBnZmFb34vIqFLqxXw+/3ShUDjcjZt5N2yE5xTv/SoR6SWiJQDO6iYoInuUUm8ppd4olUouy3SUgXaRkZGRGdVqdb6IhAtMGL9DIhKu5z+EQ0nWoq3v/wWf4hm52dSUyAAAAABJRU5ErkJggg==)](https://galaxy.ansible.com/rembik/kickstart_iso)

This role creates kickstart ISO images for RHEL/CentOS.

Requirements
------------

- Access to a repository containing ISO base images, likely on the internet.
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

kickstart_iso_name: 'CentOS 7 x86_64'
kickstart_iso_type: 'Minimal'
kickstart_iso_check_url: 'http://mirror.centos.org/centos/7/isos/x86_64/sha256sum.txt.asc'
kickstart_iso_base_url: 'http://isoredirect.centos.org/centos/7/isos/x86_64/'

# Directory where the kickstart ISO images are saved, if they do not already exist
kickstart_iso_storage: ".images/{{ kickstart_iso_name|replace(' ','-') }}"

kickstart_iso_bios_conf_file: 'isolinux/isolinux.cfg'
kickstart_iso_uefi_conf_file: 'EFI/BOOT/grub.cfg'
kickstart_iso_boot_name: "{{ kickstart_iso_name|replace(' ','\\x20') }}"

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

This is a sample playbook to create kickstart CentOS 7 ISO image on
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
                                     [dict(ip=hostvars[item].ansible_host, name=(item.split('.')[0]|lower))] }}"
      loop: "{{ groups['all'] }}"

  roles:
    - role: rembik.kickstart_iso
      vars:
        kickstart_iso_network_bootproto: 'static'
        kickstart_iso_network_static_netmask: '255.255.252.0'
        kickstart_iso_network_static_gateway: '10.0.0.1'
        kickstart_iso_network_static_nameserver:
          - '10.0.2.1'
          - '10.0.3.1'
```

Role Tests
----------

This role is tested periodically against the following Linux distributions and Ansible versions:

| Distribution ||
|---|---|
| [![DockerDistro](https://img.shields.io/badge/Alpine-latest%20%7C%20edge%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/alpine) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)](https://docs.ansible.com/) |
| [![DockerDistro](https://img.shields.io/badge/ArchLinux-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/r/archlinux/base) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)](https://docs.ansible.com/) |
| [![DockerDistro](https://img.shields.io/badge/CentOS-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/centos) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)](https://docs.ansible.com/) |
| [![DockerDistro](https://img.shields.io/badge/Debian-latest%20%7C%20unstable%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/debian) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)](https://docs.ansible.com/) |
| [![DockerDistro](https://img.shields.io/badge/Fedora-latest%20%7C%20rawhide%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/fedora) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)](https://docs.ansible.com/) |
| [![DockerDistro](https://img.shields.io/badge/openSUSE-Leap%20%7C%20Tumbleweed-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/opensuse) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)](https://docs.ansible.com/) |
| [![DockerDistro](https://img.shields.io/badge/Ubuntu-latest%20%7C%20devel%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/ubuntu) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)](https://docs.ansible.com/) |

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
