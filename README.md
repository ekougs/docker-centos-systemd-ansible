# CentOS systemd Ansible Test Image

[![Docker Automated build](https://img.shields.io/docker/automated/ekougs/centos-systemd-ansible.svg?maxAge=2592000)](https://hub.docker.com/r/ekougs/centos-systemd-ansible/)

## Build Instructions

If you want to build this image yourself, you could perform the following steps:

1. [Install Docker](https://docs.docker.com/engine/installation/).  
2. `cd` into this directory
3. Run the following command
```
docker build -t centos-systemd-ansible .
```

## Usage  

1. [Install Docker](https://docs.docker.com/engine/installation/).  
2. Pull this image from Docker Hub
```
docker pull ekougs/centos-systemd-ansible:7.4.1708
```  
3. Run a container from the image (to test Ansible roles, also add a volume mounted from your current working directory with `--volume=`pwd`:/etc/ansible/roles/role_under_test:ro`)
```
docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro ekougs/centos-systemd-ansible:7.4.1708
```  
4. Use Ansible inside the container
```
docker exec --tty [container_id] env TERM=xterm ansible --version
```  
&nbsp;&nbsp;&nbsp;&nbsp; or 
```
docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check
```  
