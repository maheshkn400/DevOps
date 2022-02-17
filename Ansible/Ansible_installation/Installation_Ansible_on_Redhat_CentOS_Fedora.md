# Installation of Ansible on Redhat, CentOS and Fedora

On CentOS:
~~~sh
$ sudo yum install epel-release
$ sudo yum install ansible
~~~
On Fedora:
~~~sh
$ sudo dnf install ansible
~~~
RPMs for RHEL 7 and RHEL 8 are available from the [Ansible Engine repository](https://access.redhat.com/articles/3174981).

To enable the Ansible Engine repository for RHEL 8, run the following command:
~~~sh
$ sudo subscription-manager repos --enable ansible-2.9-for-rhel-8-x86_64-rpms
~~~
To enable the Ansible Engine repository for RHEL 7, run the following command:
~~~sh
$ sudo subscription-manager repos --enable rhel-7-server-ansible-2.9-rpms
~~~
RPMs for currently supported versions of RHEL and CentOS are also available from EPEL.

On RHEL:
~~~sh
$ sudo yum install ansible
~~~

Configure 'sshd_config'
~~~sh
sudo vi /etc/ssh/sshd_config
PasswordAuthentication yes
~~~

Restart the 'sshd' service
~~~sh
sudo service sshd restart
~~~
OR
~~~sh
sudo systemctl restart sshd
~~~


Create a user for ansible
~~~sh
sudo  useradd ansadmin
sudo  passwd ansadmin
~~~

Add to sudo with NOPASSWD
~~~sh
sudo visudo
#add follwoing line
ansadmin	ALL=(ALL)	NOPASSWD: ALL
~~~

### Install On Other Platforms
* [Install on Debian](../Ansible_installation/Installation_Ansible_on_Debian.md)
* [Install on Ubuntu](../Ansible_installation/Installation_Ansible_on_Ubuntu.md)
* [Install on Amazon Linux](../Ansible_installation/Installation_Ansible_on_Amazon-Linux.md)
