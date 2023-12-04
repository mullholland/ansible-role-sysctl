# [Ansible role sysctl](#sysctl)

Configure sysctl settings

|GitHub|Downloads|Version|
|------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-sysctl/actions/workflows/molecule.yml/badge.svg)](https://github.com/mullholland/ansible-role-sysctl/actions/workflows/molecule.yml)|[![downloads](https://img.shields.io/ansible/role/d/mullholland/sysctl)](https://galaxy.ansible.com/mullholland/sysctl)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-sysctl.svg)](https://github.com/mullholland/ansible-role-sysctl/releases/)|
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

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-sysctl/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/mullholland/enterpriselinux)|all|
|[Amazon](https://hub.docker.com/r/mullholland/amazonlinux)|Candidate|
|[Fedora](https://hub.docker.com/r/mullholland/fedora/)|all|
|[Ubuntu](https://hub.docker.com/r/mullholland/ubuntu)|all|
|[Debian](https://hub.docker.com/r/mullholland/debian)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-sysctl/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-sysctl/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
