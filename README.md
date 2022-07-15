# [docker](#docker)

|GitHub|GitLab|
|------|------|
|[![github](https://github.com/mullholland/ansible-role-docker/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-docker/actions)|[![gitlab](https://gitlab.com/mullholland/ansible-role-docker/badges/main/pipeline.svg)](https://gitlab.com/mullholland/ansible-role-docker)|

Installs and configures Docker.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
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


## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  roles:
    - role: "mullholland.docker"
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
-   [ubi8](https://hub.docker.com/r/mullholland/docker-molecule-ubi8)
-   [fedora35](https://hub.docker.com/r/mullholland/docker-molecule-fedora35)
-   [fedora36](https://hub.docker.com/r/mullholland/docker-molecule-fedora36)

The minimum version of Ansible required is 2.10, tests have been done to:

-   The previous versions.
-   The current version.



## [Exceptions](#exceptions)

Some variations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| amazonlinux | Not compatible with official repository |
| centos-stream9 | Not compatible with official repository atm |


If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-docker/issues)

## [License](#license)

MIT


## [Author Information](#author-information)

[Mullholland](https://github.com/mullholland)

## [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
