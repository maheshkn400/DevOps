# Installation of Ansible on Amazon Linux and Amazon Linux 2

On Amazon Linux

~~~sh
sudo yum update -y
sudo yum install ansible
~~~

On Amazon Linux 2
~~~sh
sudo yum update -y
sudo amazon-linux-extras install ansible2
~~~

Check the ansible
~~~sh
ansible --version
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
* [Install on Redhad and Fedora](../Ansible_installation/Installation_Ansible_on_Redhat_CentOS_Fedora.md)
