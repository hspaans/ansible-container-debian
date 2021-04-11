# Debian Container for Molecule

An [Debian][debian] based container image for testing [Ansible][ansible] Roles with [Molecule][molecule]. The [repository][docker-debian10-ansible] from [Jeff Geerling][geerlingguy] was taken as starting point to create the repository.

## Example Molecule scenario

The example `molecule.yml` below is a scenario to run test on Debian 10 (Buster).

```yml
---
dependency:
  name: galaxy
driver:
  name: docker
lint: |
  set -e
  yamllint .
  ansible-lint
  flake8
platforms:
  - name: instance
    image: "ghcr.io/hspaans/molecule-container-debian:10"
    command: ""
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
    privileged: true
    pre_build_image: true
provisioner:
  name: ansible
verifier:
  name: testinfra
```

## Versions

The container is based on [LTS](https://en.wikipedia.org/wiki/Long-term_support) distribution versions with official support and fall within N and N-1. The *latest*-tag is an experimental tag to test future releases.

| Platform |    Version    |                                    Image                                     |
| :------: | :-----------: | :--------------------------------------------------------------------------: |
|  Debian  |  9 (Stretch)  |      [hspaans/molecule-container-debian:9][molecule-container-debian:9]      |
|  Debian  |  10 (Buster)  |     [hspaans/molecule-container-debian:10][molecule-container-debian:10]     |
|  Debian  | 11 (Bullseye) |     [hspaans/molecule-container-debian:11][molecule-container-debian:11]     |
|  Debian  | 11 (Bullseye) | [hspaans/molecule-container-debian:latest][molecule-container-debian:latest] |

[ansible]: https://github.com/ansible/ansible
[debian]: https://debian.org
[docker-debian10-ansible]: https://github.com/geerlingguy/docker-debian10-ansible
[geerlingguy]: https://github.com/geerlingguy
[molecule]: https://github.com/ansible-community/molecule
[molecule-container-debian:latest]: ghcr.io/hspaans/molecule-container-debian:latest
[molecule-container-debian:9]: ghcr.io/hspaans/molecule-container-debian:9
[molecule-container-debian:10]: ghcr.io/hspaans/molecule-container-debian:10
[molecule-container-debian:11]: ghcr.io/hspaans/molecule-container-debian:11
