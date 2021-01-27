# openSUSE Docker Images with ansible and systemd
![Build](https://github.com/hybridadmin/docker-ansible-opensuse/workflows/Build/badge.svg?branch=main)

> openSUSE Docker images to be used for testing ansible playbooks and roles.

## Quick reference

* Maintained by: [hybridadmin](https://github.com/hybridadmin)
* Where to get help: [The Docker Community Forums](https://forums.docker.com/), [Docker Community on Slack](https://dockr.ly/slack) or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)
* Where to file issues: [(issue tracker)](https://github.com/hybridadmin/docker-ansible-opensuse/issues) include the `docker` tag
* Supported architectures: [(more info)](https://github.com/docker-library/official-images#architectures-other-than-amd64) `amd64`


## Supported tags and respective `Dockerfile` links

- [`latest`, `tumbleweed`](https://github.com/hybridadmin/docker-ansible-opensuse/tree/main/tumbleweed/Dockerfile)
- [`15.2`](https://github.com/hybridadmin/docker-ansible-opensuse/tree/main/leap-15.2/Dockerfile)
- [`15.1`](https://github.com/hybridadmin/docker-ansible-opensuse/tree/main/leap-15.1/Dockerfile)

## How to Build the image

1. Install docker
   * [Linux](https://docs.docker.com/engine/install/)
   * [Windows](https://docs.docker.com/docker-for-windows/install/)
2. Clone the repo `git clone https://github.com/hybridadmin/docker-ansible-opensuse.git`
3. `cd` into the directory
4. Run `docker build -t ansible-opensuse .`

## How to use this image

Pull the image using the following command:
```console
docker pull hybridadmin/ansible-opensuse:latest
```

Run a container using the image with the following command:
```console
docker run -d --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro hybridadmin/ansible-opensuse:latest
```

Use ansible inside the container:
```console
docker exec --tty [container_id] env TERM=xterm ansible --version
docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/playbook.yml --syntax-check
```

Connect to the container:
```console
docker exec -it [container_id] /bin/bash
```
