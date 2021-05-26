# Installation of Docker on Ubuntu

### Prerequisites
### OS requirements
To install Docker Engine, one of these Ubuntu 64-bit version need:

* Ubuntu Hirsute 21.04
* Ubuntu Groovy 20.10
* Ubuntu Focal 20.04 (LTS)
* Ubuntu Bionic 18.04 (LTS)
* Ubuntu Xenial 16.04 (LTS)

Docker Engine is supported on `x86_64` (or `amd64`), `armhf`, and `arm64` architectures.

### Uninstall old versions

Older versions of Docker were called `docker`, `docker.io`, or `docker-engine`. If these are installed, uninstall them:

~~~sh
sudo apt-get remove docker docker-engine docker.io containerd runc
~~~

### Install using the repository
##### Set up the repository

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:
~~~sh
 sudo apt-get update
 sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
~~~
2. Add Docker’s official GPG key:
~~~sh
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
~~~
3. Use the following command to set up the stable repository.
~~~sh
echo \
 "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
 $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
 ~~~
4. Update `apt` package index, and install the _latest version_ of Docker Engine.
 ~~~sh
 sudo apt-get update
 sudo apt-get install docker-ce docker-ce-cli containerd.io
 ~~~
5. Start the Docker service
~~~sh
systemctl start docker
~~~
or
~~~sh
service docker start
~~~
6. Enable `docker` service to start on startup.
~~~sh
systemctl enable docker
~~~ 
