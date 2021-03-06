# EKS


Create one amazon linux 2 instance
Update AWS CLi latest version

```
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64-2.0.30.zip" -o "awscliv2.zip"
   unzip awscliv2.zip
   sudo ./aws/install
```
to verify the aws cli version

Configure IAM USer credentials in this machine

ssh the machine
sudo su -

aws configure

install kubectl version 1.20
   
   ```
   curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
   chmod +x ./kubectl
   mv ./kubectl /usr/local/bin 
   kubectl version --short --client
   
   ```
   
Setup eksctl
  ```
  curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
  sudo mv /tmp/eksctl /usr/local/bin
  eksctl version
  
  ```
 
Create your cluster and nodes
  
  ```
  eksctl create cluster --name=shivam-eksnew --region=ap-south-1 --node-type=t2.small --nodes-min=2 --nodes-max=2
  eksctl create cluster --name=shivam-ekst3 --region=ap-south-1 --node-type=t3.small --nodes-min=2 --nodes-max=2 --zones=ap-south-1a,ap-south-1b
  ```
  
Create two yml files
deployments.yml
services.yml

TO create the deployment and service

```
kubectl create -f deployments.yml
kubectl create -f services.yml

```

_To Get nodes_
 **kubectl get nodes**
_TO get pods_
** kubectl get pods**
_to Get service_
 **kubectl get svc**

_TO Get all deployment detail_
**kubectl get deploy -A**
_TO get all service details_
 **kubectl get service -A**
To Delete deployment 
**kubectl delete deployment deployemnt name**
_TO Delete service_
**kubectl delete service service name**



  
_To delete the EKS clsuter_
  **eksctl delete cluster cluster-name --region ap-south-1**
