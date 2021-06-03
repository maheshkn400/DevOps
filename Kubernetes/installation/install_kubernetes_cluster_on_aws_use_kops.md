# Install Kubernetes cluster on AWS using `kops`

1. Create Ubuntu EC2 instance

2. Install `awscli`
~~~sh
 curl https://s3.amazonaws.com/aws-cli/awscli-bundle.zip -o awscli-bundle.zip
 apt install unzip python
 unzip awscli-bundle.zip
 #sudo apt-get install unzip - if you dont have unzip in your system
 ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
~~~
3. Install `kubectl`
~~~sh
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
 chmod +x ./kubectl
 sudo mv ./kubectl /usr/local/bin/kubectl
~~~
4. Create an IAM user/role with Route53, EC2, IAM and S3 full access. In my case I create role name called `k8s-role`

5. Attach IAM user/role to ubuntu server

 **Note:** If you create IAM user with programmatic access then provide Access keys.
~~~sh
aws configure
~~~
6. Install `kops` on ubuntu instance:
~~~sh
 curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
 chmod +x kops-linux-amd64
 sudo mv kops-linux-amd64 /usr/local/bin/kops
~~~
7. Create a Route53 private hosted zone (you can create Public hosted zone if you have a domain)

8. Create an S3 bucket
~~~sh
aws s3 mb s3://dev.k8s.mkn400.tk
~~~
9. Expose environment variable:
~~~sh
#set variable for temporary up to current session or current console
export KOPS_STATE_STORE=s3://dev.k8s.mkn400.tk
~~~
or
~~~sh
#set variable for permanent
echo "export KOPS_STATE_STORE=s3://dev.k8s.mkn400.tk" >> /etc/profile
~~~
10. Create SSH keys before creating cluster
~~~sh
ssh-keygen
~~~
11. Create kubernetes cluster definitions on S3 bucket
~~~sh
kops create cluster --cloud=aws --zones=ap-southeast-1b --name=dev.k8s.mkn400.tk --dns-zone=mkn400.tk --dns private
~~~
12. Create kubernetes cluser and default it will create one master node and two worker nodes.
~~~sh
kops update cluster dev.k8s.mkn400.tk --yes
~~~
13. Validate your cluster
~~~sh
kops validate cluster
~~~
14. To list nodes
~~~sh
kubectl get nodes
~~~

**Deploying Nginx container on Kubernetes**
1. Deploying `nginx` Container
~~~sh
kubectl run sample-nginx --image=nginx --replicas=2 --port=80
kubectl get pods
kubectl get deployments
~~~
2. Expose the deployment as service. This will create an ELB in front of those 2 containers and allow us to publicly access them:
~~~sh
kubectl expose deployment sample-nginx --port=80 --type=LoadBalancer
kubectl get services -o wide
~~~
3. Don't forgot To delete cluster after practice otherwise AWS will cost
~~~sh
kops delete cluster dev.k8s.mkn400.tk --yes
~~~
