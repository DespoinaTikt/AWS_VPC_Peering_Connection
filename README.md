# AWS_VPC_Peering_Connection

In order to connect 2 VPCs and transfer data between them, I am going to create a VPC peering connection, as shown in the diagram below. This lab was part of my AWS re/Start training.

![Screenshot (262)](https://github.com/user-attachments/assets/8d8fd0a5-75b7-4eca-8048-10b9609187c3)

## Create the connection

First, I create the VPC peering connection, through the AWS Management Console. The 2 VPCs that I want to connect are the "Lab VPC", which has an Internet Gateway and an EC2 instance that sits in a public subnet, as the requester and the "Shared VPC", which has a MySQL instance sitting in a private subnet, as the accepter. After I create the connection, I need to accept the connection request, in order to establish it.

![Screenshot (247)](https://github.com/user-attachments/assets/91c8fb0f-c7c5-457b-b996-5edb96b3a3a4)
![Screenshot (248)](https://github.com/user-attachments/assets/e4a7b461-667c-474e-ad73-dab5ec01030c)
![Screenshot (250)](https://github.com/user-attachments/assets/f9f6163f-759b-42ab-a458-19507e3dd831)
![Screenshot (251)](https://github.com/user-attachments/assets/662e86d0-31c0-4043-9724-a14440501114)

## Configure route tables

Then I go to my route tables in order to update them with the peering connection. First, in the "Lab VPC" route table, I add a route with the destination of the peering connection. I do the same with the "Shared VPC".

![Screenshot (252)](https://github.com/user-attachments/assets/5b0e6437-2bff-4ab3-9280-a982173583bb)
![Screenshot (253)](https://github.com/user-attachments/assets/a54a9f5d-ec2e-428a-9050-2d8def7c74eb)
![Screenshot (255)](https://github.com/user-attachments/assets/abfec4f4-e559-42aa-b27c-175422b0a842)

## Test the connection

In order to test the VPC peering connection, I go to my EC2 instances. There I have the App Server, in the "Lab VPC" which is a public instance. I retrieve the public IP address and connect to it. 

![Screenshot (256)](https://github.com/user-attachments/assets/46de900d-fe2b-40f4-b057-a5af697034ef)
![Screenshot (257)](https://github.com/user-attachments/assets/bebeb042-86ed-4cb3-a6f3-f5732b2d6cb8)

In the Settings, I provide the appropriate credentials. Then, the application shows data retrieved from the database, which sits in the "Shared VPC". This step confirms that the VPC peering connection was established because "Shared VPC" does not have an Internet Gateway. The only way to access the database is through the VPC peering connection.

![Screenshot (258)](https://github.com/user-attachments/assets/f2ecb9bb-36f4-4ef2-a789-2d9276acfd1d)
![Screenshot (259)](https://github.com/user-attachments/assets/ac80e377-29c4-47c8-94ee-6e8b9492c141)


