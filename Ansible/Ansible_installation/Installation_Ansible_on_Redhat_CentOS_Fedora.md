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

### Install On Other Platforms
* [Install on Debian](../Ansible_installation/Installation_Ansible_on_Debian.md)
* [Install on Ubuntu](../Ansible_installation/Installation_Ansible_on_Ubuntu.md)
