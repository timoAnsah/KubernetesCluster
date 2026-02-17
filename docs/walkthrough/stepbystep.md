Deploy Kubernetes Cluster using EKS. EKS is AWSs service for deploying Kubernetes Clusters in the cloud.

## Step 1 - Launch & Connect to an EC2 instance
In this step I will launch & connect to an EC2 Instance. This is because it will be my central development workspace for sending commands & creating Kubernetes Clusters.

<img width="1763" height="207" alt="EC2launch" src="https://github.com/user-attachments/assets/c12909cd-e509-4e3c-bc3a-914bfac7a104" />


My EC2 Instance is called `eks-instance` & for the Amazon Mchine Image I selected `Amazon Linux 2023 AMI`
An AMI is a template or blueprint used to create EC2 Instance. The image defines EC2 instance OS with the application needed to launch the instance.

<img width="817" height="710" alt="EC2 Config" src="https://github.com/user-attachments/assets/2a71452e-296c-4794-99c6-8d6af1345d4e" />

For instance type, I selected a `T2 Micro`. AMIs define what pre built software & operating systems your server runs. 
Instance type defines how fast & powerful the server runs & covers the hardware componenets, CPU power, memory size & storage space. T2 Micro is affordable for light use.

<img width="725" height="852" alt="EC2Launch2" src="https://github.com/user-attachments/assets/8f89000f-a4dd-4cd9-9464-de658c222115" />


Key pair: A key pair is like a lock & key for EC2 Instance. Usually a key pair is not essential to SSH connect to an instance
I Kept the default values in Network settings and allow SSH Traffic. 
Security group allows SSH Traffic from anywhere (0.0.0.0/0). 
This is not best security practise but I will leave this temporarily to make connecting via SSH easier.
