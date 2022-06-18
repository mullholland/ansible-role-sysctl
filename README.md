# [sysctl](#sysctl)

|GitHub|GitLab|
|------|------|
|[![github](https://github.com/mullholland/ansible-role-sysctl/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-sysctl/actions)|[![gitlab](https://gitlab.com/mullholland/ansible-role-sysctl/badges/master/pipeline.svg)](https://gitlab.com/mullholland/ansible-role-sysctl)|[![quality](https://img.shields.io/ansible/quality/unset)](https://galaxy.ansible.com/mullholland/sysctl)|

description

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# Reload the sysctl after cahnging values
# /sbin/sysctl -p
sysctl_reload: true

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


## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
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

  roles:
    - role: "mullholland.sysctl"
```





## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

-   [debian9](https://hub.docker.com/r/mullholland/docker-molecule-debian9)
-   [debian10](https://hub.docker.com/r/mullholland/docker-molecule-debian10)
-   [debian11](https://hub.docker.com/r/mullholland/docker-molecule-debian11)
-   [ubuntu1804](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu1804)
-   [ubuntu2004](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu2004)
-   [ubuntu2204](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu2204)
-   [centos7](https://hub.docker.com/r/mullholland/docker-molecule-centos7)
-   [centos-stream8](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream8)
-   [centos-stream9](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream9)
-   [ubi8](https://hub.docker.com/r/mullholland/docker-molecule-ubi8)
-   [fedora35](https://hub.docker.com/r/mullholland/docker-molecule-fedora35)
-   [fedora36](https://hub.docker.com/r/mullholland/docker-molecule-fedora36)
-   [amazonlinux](https://hub.docker.com/r/mullholland/docker-molecule-amazonlinux)
-   [rockylinux8](https://hub.docker.com/r/mullholland/docker-molecule-rockylinux8)
-   [almalinux8](https://hub.docker.com/r/mullholland/docker-molecule-almalinux8)

The minimum version of Ansible required is 2.10, tests have been done to:

-   The previous versions.
-   The current version.
-   The [devel](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-devel-from-github-with-pip) version.





If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-sysctl/issues)

## [License](#license)

MIT


## [Author Information](#author-information)

[Mullholland](https://github.com/mullholland)

## [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
