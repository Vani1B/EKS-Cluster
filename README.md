# EKS-Cluster
First create IAM roles are necessary for granting cluster nodes and worker nodes proper permissions.

![image](https://github.com/user-attachments/assets/6297b744-fb51-4bcd-99cc-25e6f6d016f4)

![image](https://github.com/user-attachments/assets/2bdf223d-39d1-44d6-8431-70928fd0dfca)


Update the script with the correct ARN, subnet IDs, and region.

aws eks create-cluster \
  --name my-cluster \
  --role-arn arn:aws:iam::194722428485:role/AmazonEKSAutoClusterRole-vani \
  --resources-vpc-config subnetIds=subnet-0cf54daad10f7322a,subnet-0580d8ac907af6c11,subnet-07f6ee2d7724b0fbd \
  --region us-east-1


aws eks create-nodegroup \
  --cluster-name my-cluster \
  --nodegroup-name my-nodegroup \
  --subnets subnet-0cf54daad10f7322a subnet-0580d8ac907af6c11 subnet-07f6ee2d7724b0fbd \
  --instance-types t3.medium \
  --node-role arn:aws:iam::194722428485:role/AmazonEKSAutoNodeRole-vani \
  --scaling-config minSize=1,maxSize=3,desiredSize=2 \
  --region us-east-1

aws eks update-kubeconfig \
  --region us-east-1 \
  --name my-cluster

Create cluster by updating roles

![image](https://github.com/user-attachments/assets/8b1b8ffc-4a6d-4469-be6d-23950eef8ad8)

Create nodegroup using script in the cli

![image](https://github.com/user-attachments/assets/4c75759f-d0ed-4cef-99ec-a9273ef853bb)

![image](https://github.com/user-attachments/assets/d5dd685d-5b74-40a6-a10e-e1128c05acc8)

Creating pods

![image](https://github.com/user-attachments/assets/7d4193f9-4dfb-4708-8228-e5e048040bc5)

Creating deployment
![image](https://github.com/user-attachments/assets/def4499d-127b-4625-a312-02ff5c21f175)

Lets update the nginx pods to use the imagef ngnix:1.16.1

![image](https://github.com/user-attachments/assets/f5943f74-8e8e-46c1-91f4-895240e2497b)

To get the details of Deployment

![image](https://github.com/user-attachments/assets/398e5344-bc47-4343-80f5-e6d07edbc7ed)

![image](https://github.com/user-attachments/assets/9fed0c65-3c95-4b23-8e52-ba31908993c1)
















