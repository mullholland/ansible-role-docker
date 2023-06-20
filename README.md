# [docker](#docker)

Installs and configures Docker.

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-docker/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-docker/actions)|[![gitlab](https://gitlab.com/opensourceunicorn/ansible-role-docker/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-docker)|[![quality](https://img.shields.io/ansible/quality/57468)](https://galaxy.ansible.com/mullholland/docker)|[![downloads](https://img.shields.io/ansible/role/d/57468)](https://galaxy.ansible.com/mullholland/docker)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-docker.svg)](https://github.com/mullholland/ansible-role-docker/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-docker/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  roles:
    - role: "mullholland.docker"
```


## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-docker/blob/master/defaults/main.yml):

```yaml
---
# Edition can be one of: 'ce' (Community Edition) or 'ee' (Enterprise Edition).
docker_edition: 'ce'
docker_packages:
  - "docker-{{ docker_edition }}"
  - "docker-{{ docker_edition }}-cli"
  - "containerd.io"
docker_package_state: present

# Docker Compose options.
docker_install_compose: true
docker_compose_version: "2.1.1"
docker_compose_url: "https://github.com/docker/compose/releases/download/v{{ docker_compose_version }}/docker-compose-linux-x86_64"
docker_compose_path: "/usr/local/bin/docker-compose"

# Used only for Debian/Ubuntu. Switch 'stable' to 'edge' if needed.
docker_apt_repo_key_url: "https://download.docker.com/linux/ubuntu/gpg"
docker_apt_release_channel: stable

# Used only for RedHat/CentOS.
docker_yum_repo_key_url: "https://download.docker.com/linux/centos/gpg"
docker_yum_repo__url: "https://download.docker.com/linux/centos/docker-{{ docker_edition }}.repo"

# Adding existing user to docker group
docker_add_users: []
#  - ansible
#  - ansiblemgmt

# Where the ENV file is saved
docker_opts_path: "/etc/docker"
# If you want to specify any docker options this variable has to be a list:
docker_opts_common: []
#  - "-H fd://"
docker_opts_individual: []
# - "--insecure-registry myregistrydomain.com:5000"
# - "--ipv6"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-docker/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-docker/png/requirements.png "Dependencies")

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

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-docker/issues)

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-docker/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)

Please consider [sponsoring me](https://github.com/sponsors/mullholland).
