# Docker Commands

Show installed docker version
~~~sh
docker version
~~~
login to your docker hub
~~~sh
docker login
~~~
search image
~~~sh
docker search <image-name>
~~~
pull the image
~~~sh
docker pull <image-name>
~~~
pull image from your repo
~~~sh
docker pull <login-id/repo-name:imagename>
docker pull mkn400/webapp_demo
~~~
## Docker image

Create Dockerfile
~~~sh
vi Dockerfile
 FROM busybox
 CMD echo "Hello world! This is my first Docker image."
~~~
Build image from `Dockerfile`
~~~sh
docker build .
~~~
re-tagging
~~~sh
docker -t <image> <newimage>
docker -t ubuntu ubuntu:20.04
~~~
re-tagging for your docker repo
~~~sh
docker -t <existing-image> <hub-user/repo-name:tag>
docker -t ubuntu mkn400/ubuntu:20.04
~~~
commit the changes before push
~~~sh
docker commit <hub-user/repo-name:tag>
docker commit mkn400/ubuntu:20.04
~~~
Create image from container
~~~sh
docker commit CONTAINER-NAME <docker_account_id>/container:<tage_name>
docker commit webapp mkn400/ubuntu:apache2
~~~
save image to tar file
~~~sh
docker save image >> file
docker save nginx >> nginx.tar
~~~
Load an image from tar file
~~~sh
docker load -i TARFILE
docker load -i nginx.tar
~~~
push image to your docker repo
~~~sh
docker push <docker-username>/<image-name:tag-name>
docker push mkn400/simple-projects:myimage
~~~
Delete an image
~~~sh
docker rmi <image-name>
~~~
Show a list of all images
~~~sh
docker images
~~~
Delete danging images
~~~sh
docker image prune
~~~
Delete all unused images
~~~sh
docker image prune -a
~~~

## Docker Containers

start a new container from image
~~~sh
docker run image
docker run nginx
~~~
assign name to container
~~~sh
docker run --name container-name image
docker run --name web nginx
~~~
map a ports to container
~~~sh
docker run -p HOST-PORT:CONTAINER-PORT IMAGE
docker run -p 8080:80 nginx
~~~
map all ports
~~~sh
docker run -P image
docker run -P nginx
~~~
assign a hostname
~~~sh
docker run --hostname HOSTNAME image
docker run --hostname srv nginx
~~~
add --dns entry
~~~sh
docker run --add-host HOSTNAME:ip image
docker run --add-host ns1:1.2.3.4 nginx
~~~
map a local directory to container
~~~sh
docker run -v HOSTDIR:CONTAINEDIR IMAGE
docker run -v ~/:/usr/share/nginx/html nginx
~~~
map a docker volume to the container
~~~sh
docker run -v <VOLUMENAME>:<CONTAINER-DIR>
docker run -v nginxhtml:/usr/share/nginx/html
#if the volume not available automaticaly volume will create
~~~
change the entrypoint
~~~sh
docker run -it --entrypoint EXECUTABLE IMAGE
docker run -it --entrypoint bash nginx
~~~
run contaner in detach mode
~~~sh
docker run -d IMAGE
docker run -d nginx
~~~

## Manage Containers

Show a list of containers
~~~sh
docker ps
~~~
Show list of all containers
~~~sh
docker ps -a
~~~
Delete a container
~~~sh
docker rm CONTAINER / ID
docker rm web
~~~
Delete running container
~~~sh
docker stop <CONTAINER-NAME / ID >
docker rm <CONTAINER-NAME / ID >
docker stop web
docker rm web
~~~
OR
~~~sh
docker rm -f CONTAINER / ID
docker rm -f web
~~~
Delete stoped containers
~~~sh
docker container prune
~~~
Stop a running container
~~~sh
docker stop CONTAINER
docker stop web
~~~
Start a stoped container
~~~sh
docker start CONTAINER
docker start web
~~~
Copy a file from container to host
~~~sh
docker cp CONTAINER:SOURCE TARGET
docker cp web:/index.html index.html
~~~
Copy a file from container to host
~~~sh
docker cp TARGET CONTAINER:SOURCE
docker cp index.html web:/index.html
~~~
Start a shell inside a running container
~~~sh
docker -it CONTAINER EXECUTABLE
docker -it web bash
~~~
Rename a container
~~~sh
docker rename OLD_NAME NEW_NAME
docker rename 096 web
~~~
or
~~~sh
docker rename web webapp
~~~
Create an image out of container
~~~sh
docker commit CONTAINER
docker commit web
~~~

## info & status

Show the logs of the container
~~~sh
docker logs CONTAINER-NAME
docker logs web
~~~
Show the status of running containers
~~~sh
docker status
~~~
Show the processes of container
~~~sh
docker top CONTAINER-NAME
docker top web
~~~
Get detailed information of object
~~~sh
docker inspect CONTAINER-NAME
docker inspect web
~~~
Show all modified files in container
~~~sh
docker diff CONTAINER-NAME
docker diff web
~~~
Show mapped ports of container
~~~sh
docker port CONTAINER-NAME
docker port web
~~~

Docker Volumes
Docker Networking

## Simple Project WordPress
The projects contains two container of httpd and mysql integrated each.
