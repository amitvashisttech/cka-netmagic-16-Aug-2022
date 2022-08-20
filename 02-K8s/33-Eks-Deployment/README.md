# Amazon Cloud Access

## Craete a Programatic Access Key User

```
You need to a IAM User - > Login -> AWS Console -> Search (IAM) -> Create User (yourlabusername) -> Enable Progrmatic Access -> Create & Downloand Keys.

```

## Now export the AWS Keys into Env. Variables

```
echo "export AWS_ACCESS_KEY_ID="XXXXXXXXXXXX" " >> .bashrc
```

```
echo "export AWS_SECRET_ACCESS_KEY="XXXXXXYYYYYYYYYYYYYYYYYYYYYYYYYYY" " >>  .bashrc
```

```
source  .bashrc
```

```
set | grep -i AWS
```

## Download EKSCTL Binary from the following Sources: 

1. Download and extract the latest release of eksctl with the following command.

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
```

2. Move the extracted binary to /usr/local/bin.
```
sudo mv /tmp/eksctl /usr/local/bin
```

3. Test that your installation was successful with the following command.
```
eksctl version
```

## Download Kubectl Binary also, if you already have the skip: 

## Installing aws-iam-authenticator App. 
1. Download the Amazon EKS vended aws-iam-authenticator binary from Amazon S3 for your hardware platform.
```
curl -o aws-iam-authenticator https://amazon-eks.s3.us-west-2.amazonaws.com/1.21.2/2021-07-05/bin/linux/amd64/aws-iam-authenticator
```

2. Apply execute permissions to the binary.
```
chmod +x ./aws-iam-authenticator
```

3. Copy the binary to a folder in your $PATH. We recommend creating a $HOME/bin/aws-iam-authenticator and ensuring that $HOME/bin comes first in your $PATH.
```
mkdir -p $HOME/bin && cp ./aws-iam-authenticator $HOME/bin/aws-iam-authenticator && export PATH=$PATH:$HOME/bin
```


## Let's set up EKS Cluster:

```
# eksctl create cluster --name <cluster-name> --version 1.21 --region <region> --nodegroup-name worker-nodes --node-type t2.micro --nodes 2
```

```
# eksctl create cluster --name k8s-av-user26 --version 1.21 --region us-east-2 --nodegroup-name worker-nodes --node-type t2.micro --nodes 2
```


## Check the status of EKS K8s Cluster
```
kubectl get nodes
```
```
root@master: # kubectl get nodes
NAME                                           STATUS   ROLES    AGE   VERSION
ip-192-168-61-124.us-east-2.compute.internal   Ready    <none>   10m   v1.21.5-eks-9017834
ip-192-168-83-199.us-east-2.compute.internal   Ready    <none>   10m   v1.21.5-eks-9017834
root@master: #
```

