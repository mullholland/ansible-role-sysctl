# [sysctl](#sysctl)

Configure sysctl settings

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-sysctl/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-sysctl/actions)|[![gitlab](https://gitlab.com/opensourceunicorn/ansible-role-sysctl/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-sysctl)|[![quality](https://img.shields.io/ansible/quality/58721)](https://galaxy.ansible.com/mullholland/sysctl)|[![downloads](https://img.shields.io/ansible/role/d/58721)](https://galaxy.ansible.com/mullholland/sysctl)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-sysctl.svg)](https://github.com/mullholland/ansible-role-sysctl/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-sysctl/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  vars:
    sysctl_settings:
      - name: "vm.swappiness"
        value: 10
        state: "present"
        reload: "true"
        ignoreerrors: false
        sysctl_file: "/etc/sysctl.conf"
        sysctl_set: true
      - name: vm.vfs_cache_pressure
        value: 50
      - name: "net.ipv4.ip_forward"
        value: 1

  pre_tasks:
    - name: show virtualization type fot Ansible role testing
      ansible.builtin.debug:
        msg: "{{ ansible_virtualization_type }}"

  roles:
    - role: "mullholland.sysctl"
```


## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-sysctl/blob/master/defaults/main.yml):

```yaml
---
sysctl_settings: []
#  - name: "vm.swappiness"            # required
#    value: 10                        # required
#    state: "present"                 # optional => default('present')
#    reload: "true"                   # optional => default('true')
#    ignoreerrors: false              # optional => default('false')
#    sysctl_file: "/etc/sysctl.conf"  # optional => default('/etc/sysctl.conf')
#    sysctl_set: true                 # optional => default('false')
#  - name: vm.vfs_cache_pressure
#    value: 50
#  - name: "net.ipv4.ip_forward"
#    value: 1
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-sysctl/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-sysctl/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/mullholland/docker-centos-systemd/general)|all|
|[Amazon](https://hub.docker.com/repository/docker/mullholland/docker-amazonlinux-systemd/general)|Candidate|
|[Fedora](https://hub.docker.com/repository/docker/mullholland/docker-fedora-systemd/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/mullholland/docker-ubuntu-systemd/general)|all|
|[Debian](https://hub.docker.com/repository/docker/mullholland/docker-debian-systemd/general)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-sysctl/issues)

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-sysctl/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)

Please consider [sponsoring me](https://github.com/sponsors/mullholland).
