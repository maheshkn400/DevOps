# Installation of Docker on Amazon Linux

It is a standard method of installing [Docker](https://www.docker.com/) on [Amazon Linux](https://aws.amazon.com/amazon-linux-ami/) [EC2](https://aws.amazon.com/ec2/)

1. Update packages
~~~sh
sudo yum update -y
~~~
2. Install Docker
On Amazon Linux
~~~sh
sudo yum install -y
~~~
On Amazon Linux 2
~~~sh
sudo amazon-linux-extras install docker
~~~
3. Start the Docker service
~~~sh
sudo service docker start
~~~
or
~~~sh
sudo systemctl start docker
~~~
4. Enable `docker` server start on system startup.
~~~sh
sudo systemctl enable docker
~~~
5. Verify that docker is installed correctly by running the hello-world image.
~~~sh
sudo docker run hello-world
~~~

NOTE:
* If you are not using `root` user no need to use `sudo` in front of commads.
* In realtime envirnoment we are not install docker in `Amazon linux` we had separate containerization services called [Amazon Elastic Container Registry (ECR)](https://aws.amazon.com/ecr/?c=cn&sec=srv), [Amazon Elastic Container Service (ECS)](https://aws.amazon.com/ecs/?c=cn&sec=srv&whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc&ecs-blogs.sort-by=item.additionalFields.createdDate&ecs-blogs.sort-order=desc), [Amazon Elastic Kubernetes Service (EKS)](https://aws.amazon.com/eks/?c=cn&sec=srv&whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc&eks-blogs.sort-by=item.additionalFields.createdDate&eks-blogs.sort-order=desc) and so on.


### Install On Other Platforms
* [Install on CentOS and Fedora](./install_docker_on_centos_fedora.md)
* [Install on Ubuntu](./install_docker_on_ubuntu.md)
