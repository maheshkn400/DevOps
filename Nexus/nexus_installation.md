# Nexus Installation
Nexus is one a artifact repository which helps to store your build outcomes.  

### Prerequisites

1. EC2 instance with java

### Implementation steps

Download and setup nexus stable version
~~~sh
cd /opt
wget https://sonatype-download.global.ssl.fastly.net/nexus/3/nexus-3.0.2-02-unix.tar.gz
tar -zxvf  nexus-3.0.2-02-unix.tar.gz
mv /opt/nexus-3.0.2-02 /opt/nexus
~~~

As a good security practice, it is not advised to run nexus service as root. so create new user called nexus and grant sudo access to manage nexus services
~~~sh
sudo adduser nexus
# visudo \\ nexus   ALL=(ALL)       NOPASSWD: ALL
sudo chown -R nexus:nexus /opt/nexus
~~~

Open /opt/nexus/bin/nexus.rc file, uncomment run_as_user parameter and set it as following.
~~~sh
vi /opt/nexus/bin/nexus.rc
run_as_user="nexus" (file shold have only this line)
~~~

Add nexus as a service at boot time
~~~sh
sudo ln -s /opt/nexus/bin/nexus /etc/init.d/nexus
~~~
Login as a nexus user and start service
~~~sh
su - nexus
service nexus start
~~~

Login nexus server from browser on port `8081`

`http://<Nexus_server_IP:8081`

Use default credentials to login

username : admin  
password : admin123


### Troubleshooting

Service is not starting ?
- Make sure you are trying to start service with nexus user.
- Check java installed

Unable to access nexus URL?
- Make sure port 8081 is opened in security group.

_I'm Happy To Get [Suggestions](https://forms.gle/TbfdXQ5H3a3oSTjo6)_ :smile:
