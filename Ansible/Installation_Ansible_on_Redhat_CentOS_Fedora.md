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
:eight_pointed_black_star: RPMs for currently supported versions of RHEL and CentOS are also available from [EPEL](https://fedoraproject.org/wiki/EPEL). :eight_pointed_black_star:
