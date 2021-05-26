# Installation of Docker on CentOS and Fedora

**Table of content**
<!--ts-->
* [Prerequisites](#Prerequisites)
* [Uninstall old versions](#uninstall_old)
* [Set up the repository](#set_repository)
* [Install Docker engine](#install_docker)
<!--te-->
<a name="Prerequisites"></a>

## Prerequisites

The `centos-extras` repository must be enabled. By default it is enabled, but if you have disabled it, you need to re-enable it.

<a name="uninstall_old"></a>

## Uninstall old versions

Older versions of Docker were called `docker` or `docker-engine`. If these are installed, uninstall them, along with associated dependencies.
~~~sh
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
~~~
It’s OK if `yum` reports that none of these packages are installed.

The contents of /var/lib/docker/, including images, containers, volumes, and networks, are preserved. The Docker Engine package is now called docker-ce.

<a name="set_repository"></a>

## Set up the repository

Install the `yum-utils` package (which provides the `yum-config-manager` utility) and set up the stable repository.
~~~sh
 sudo yum install -y yum-utils
 sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
~~~

enables the docker `nightly` repository.
~~~sh
sudo yum-config-manager --enable docker-ce-nightly
~~~

<a name="install_docker"></a>

## Install Docker Engine

1. Install the latest version of Docker Engine and containerd, or go to the next step to install a specific version:
~~~sh
sudo yum install docker-ce docker-ce-cli containerd.io
~~~
If prompted to accept the GPG key, verify that the fingerprint matches 060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35, and if so, accept it.

2. Start Docker.
~~~sh
sudo systemctl start docker
~~~
3. Enable `docker` service on system startup.
~~~sh
sudo systemctl enable docker
~~~
4. Verify that Docker Engine is installed correctly by running the `hello-world` image.
~~~sh
 sudo docker run hello-world
~~~
