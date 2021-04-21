# Docker commands for reference

Pull a base image.
~~~sh
$ docker pull ubuntu
~~~
To create a Container.
~~~sh
$ docker run -d -it ubuntu /bin/bash
~~~
To stop a Container.
~~~sh
$ docker stop container_id
~~~
To restart a Container.
~~~sh
$ docker restart container_id
~~~
To Connect to a running Container.
~~~sh
$ docker attach container_id
~~~
To copy a file from a container to the host, you can use the command
~~~sh
$ docker cp containerId:/file/path/within/container /host/path/target
~~~
Copying files from host to docker container
~~~sh
$ docker cp foo.txt mycontainer:/foo.txt$ docker cp mycontainer:/foo.txt foo.txt
~~~
How to mount host directory in docker container?
~~~sh
$ docker run -v /host/directory:/container/directory image_name command_to_run$ docker run -d -it -v /usr/kishore/main_folder:/test_container ubuntu /bin/bash Example docker run --name myjenkins -p 8080:8080 -p 50000:50000 -v /var/jenkins_home jenkins
~~~
To delete a Container?
~~~sh
$ docker rm container_id
~~~
To show running Containers. With -a option, it shows running and stopped Containers.
~~~sh
$ docker ps
~~~
To show Container information like IP adress.
~~~sh
$ docker inspect container_id
~~~
