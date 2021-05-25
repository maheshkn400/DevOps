# Installation of Ansible on Debian

Debian users may leverage the same source as the Ubuntu PPA.

Add the following line to ``/etc/apt/sources.list`:
~~~
deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main
~~~
Set `apt keys`
~~~sh
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
$ sudo apt update
$ sudo apt install ansible
~~~

:arrow_right: [Ansible](https://github.com/maheshkn400/DevOps/tree/master/Ansible) or [DevOps :house: ](https://github.com/maheshkn400/DevOps/)
