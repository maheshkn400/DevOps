# Simple DevOps Project 2

In this project we are creating Jenkins CI CD of `git` > `github` > `jenkins` > `maven` to build and send `.war` file > to `ansible server` and deploy `.war` file with playbook > to  `tomcat 8 server`.

![simple devops project 2](./img/devops-2.png)

**Prerequisites**

- [Ansible server ](../../Ansible/Ansible_installation/)
  - [Create playbook](#playbook)
- [Jenkins Server](../../Jenkins/Jenkins_installation.md)
  - Intall [Publish over ssh](#publish_over_ssh) Plugin
  - [Enable connection](#enable_ssh) between Ansible and Jenkins
- [Tomcat Server](../../Tomcat/tomcat8_installation.md)

<a name="playbook"></a>
**Create Playbooks**

Create dicrectory `playbooks` on `/opt`
~~~sh
mkdir /opt/playbooks
~~~
Create a `copywarfile.yml` playbook file under `/opt/playbooks` directory on Ansible server
~~~sh
# copywarfile.yml
---
- hosts: all
  become: true
  tasks:
    - name: copy jar/war onto tomcat servers
        copy:
          src: /op/playbooks/wabapp/target/webapp.war
          dest: /opt/apache-tomcat-8.5.32/webapps
~~~
Add tomcat server details to /etc/ansible/hosts (if you are using other hosts file update server info there)
~~~sh
echo "<server_IP>" >> /etc/ansible/hosts
~~~

<a name="publish_over_ssh"></a>
**Install "publish Over SSH"**

Jenkins Dashboard >> `Manage Jenkins` > `Manage Plugins` > `Available` > `Publish over SSH`

<a name="enable_ssh"></a>
**Enable connection between Ansible and Jenkins**

Jenkins Dashboard >> `Manage Jenkins` > `Configure System` > `Publish Over SSH` > `SSH Servers`

- SSH Servers:
  - Hostname:``<ServerIP>``
  - username: `ansadm`
  - password: `*******`

Test the connection by clicking `Test Connection` and save

**Jenkins CI CD new item Setup**

Create Jenkins job, Fill the following details,
- Jenksing Dashboard > click `New Item`
  - Enter item name: `sample devops project 1`
  - Source Code Management:
    - Repository: `https://github.com/maheshkn400/hello-world.git`
    - Branches to build : `*/master`
  - Build:
    - Root POM:`pom.xml`
    - Goals and options : `clean install package`

  - Add post-build steps
    - Send files or execute commands over SSH
      - SSH Server : `ansible_server`
      - Source fiels: `webapp/target/*.war`
      - Remote directory: `//opt//playbooks`
  - Add post-build steps
    - Send files or execute commands over ssH
      - SSH Server : `ansible_server`
      - Exec command: `ansible-playbook /opt/playbooks/copywarfile.yml`

Run the job and you should be able to seen build has been deployed on Tomcat server.

_I'm Happy To Get [Suggestions](https://forms.gle/TbfdXQ5H3a3oSTjo6)_ :smile:
