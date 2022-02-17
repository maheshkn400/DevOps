# Installation of Ansible on Debian

Debian users may leverage the same source as the Ubuntu PPA.

Add the following line to /etc/apt/sources.list`:
~~~
deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main
~~~
Set `apt keys`
~~~sh
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
$ sudo apt update
$ sudo apt install ansible
~~~

### Install On Other Platforms
* [Install on Redhat, CentOS and Fedora](../Ansible_installation/Installation_Ansible_on_Redhat_CentOS_Fedora.md)
* [Install on Ubuntu](../Ansible_installation/Installation_Ansible_on_Ubuntu.md)
* [Install on Amazon Linux](../Ansible_installation/Installation_Ansible_on_Amazon-Linux.md)
