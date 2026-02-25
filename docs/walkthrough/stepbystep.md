Deploy Kubernetes Cluster using EKS. EKS is AWSs service for deploying Kubernetes Clusters in the cloud.

## Step 1 - Launch & Connect to an EC2 instance
In this step I will launch & connect to an EC2 Instance. This is because it will be my central development workspace for sending commands & creating Kubernetes Clusters.

<img width="1763" height="207" alt="EC2launch" src="https://github.com/user-attachments/assets/c12909cd-e509-4e3c-bc3a-914bfac7a104" />


My EC2 Instance is called `eks-instance` & for the Amazon Mchine Image I selected `Amazon Linux 2023 AMI`
An AMI is a template or blueprint used to create EC2 Instance. The image defines EC2 instance OS with the application needed to launch the instance.

<img width="817" height="710" alt="EC2 Config" src="https://github.com/user-attachments/assets/2a71452e-296c-4794-99c6-8d6af1345d4e" />

For instance type, I selected a `T2 Micro`. AMIs define what pre built software & operating systems your server runs. 
Instance type defines how fast & powerful the server runs & covers the hardware componenets, CPU power, memory size & storage space. T2 Micro is affordable for light use.

<img width="539" height="875" alt="EC2Launch2" src="https://github.com/user-attachments/assets/d37af729-876b-4bc5-af9d-87f917762abe" />

Key pair: A key pair is like a lock & key for EC2 Instance. Usually a key pair is not essential to SSH connect to an instance
I Kept the default values in Network settings and allow SSH Traffic. 
Security group allows SSH Traffic from anywhere (0.0.0.0/0). 
This is not best security practise but I will leave this temporarily to make connecting via SSH easier.

Now that my Instance is running, I will connect to it using EC2 Instance Connect.

EC2 Instance connect is a shortcut way to get direct SSH access to my EC2 Instance.
so instead of having to manage key pairs manually, Instance Connect connects me to Instances I have created already.
This skips generating jey pairs, associating the public key with my EC2 Instance, setting up an SSH Client & running SSH commands to set up a SSH connection.

We begin by selecting the `eks-instance` & selecting connect

<img width="1757" height="155" alt="EC2 instance connect" src="https://github.com/user-attachments/assets/58f49fda-cefb-46ff-bdd5-bbfd2b668516" />


<img width="1107" height="485" alt="instanceConnect" src="https://github.com/user-attachments/assets/325760fc-a6ec-4c6b-bcc0-1e336911782d" />

This is the `Instance Connect` page, AWS gives you different options to connect with your EC2 Instance.

<img width="3805" height="1550" alt="eks-instance" src="https://github.com/user-attachments/assets/635de451-aaff-419f-a8f1-692203afe0be" />

EC2 Instance Connect uses a whole range of IP Addresses & they vary depending on your region.
I kept the default security group for my develoment instance because i was not certain which IP Addreesses my Instances should be allowing for SSH Traffic.
This can be improved by tailoring the inbound rules of my security group to EC2 Instance connect.


## Step 2 - Launching EKS Cluster
In this next step I will launch an EKS Cluster with the command line too `EKSCTL` to send commands to the EC2 Instance & create clusters 

`EkSCTL` is a command line tool used to create & manage EKS clusters.
It simplifies the process of setting up & configuring EKS clusters.

Kubernetes is a tool used to manage running containers.
Once applications are containerised, Kubernetes helps them run smoothly by handling tasks like load balancing, scaling & restarting the containers when they fail.
It does not build containers, Docker handles that. 

setting up Kubernetes from scratch can be time consuming & complex because you'll need to configure Kubernetes networking, scaling & security settings manually. 
EKS handles these set up tasks & aids integration with other AWS services.

