# AWS-VPC-simplified
This repo describes about AWS VPC key concepts


<img width="468" alt="image" src="https://user-images.githubusercontent.com/14869837/115114132-0a1ab300-9f64-11eb-98f0-31eb9b3c36a4.png">


# VPC
 VPC is virtual private cloud similar to an on-prime environment but hosted in the cloud environment. It’s simple to create a VPC on AWS. The only new specification required is to provide the CIDR block value.
1.	CIDR block defines the of range of ip address that can be used in the VPC.
2.	Other settings are straight forward just defining the values and names required.
Elastic IP address
Elastic ip address are used to provide 

# subnets (private and public)
The subnets are used to launch an instance in the VPC, without a subnet no EC2 instances can be lunched in a VPC.
So, it is mandatory to have a subnet in order to launch an instance in VPC.
A subnet can be private or public, The key difference between them are:
•	In a private subnet, All the instances that are present in a private subnet cannot access the internet directly, whereas in a public subnet the instances can access the internet using internet gateways.
•	Every subnet can be associated with a single route table. However, multiple subnets can use same route tables.

# Internet Gateway
Internet gateway provided access to the internet using the route tables. 
•	Creating an internet gateway is straight forward. Provide the name of the Internet Gateway(IGW).
•	Then the IGW needs to be attached with the VPC to which it has to be used.
•	By doing so the route table can access the instances that are present in the subnets of that VPC. This helps to route traffic from outside world to public subnets.

# Nat Gateway 
A Nat device helps private subnets to access internet, by using Nat devices you can provide access from the private subnet to the internet. However, It doesn’t allow the internet to access the private subnet.
•	for example, if a private subnet required access to other aws services it can use nat device.
•	To create a Nat Gateway, you need to provide access to public subnet. This in turn helps you the private subnet to access the internet.

# Security groups 
Security groups sits on top of subnets as a additional security layer,Rules are defined in the security groups to allow traffic from specific resources.
For example: A security group can communicate with specific security group like the web server and public subnets can be defined in a public subnet with security group rules allowing traffic from http and https connections.
Conversely, A security group can be created for private subnet where web servers can be hosted with inbound traffic accepting only from the public security group.

# Network ACL’s
ACL’s sits between route table and subnet similar to route table we defined.We set the inbound and outbound rules to restrict traffic into the subnet.This is an extra added layer of security.

# Best Practices:

•	Use Nat Gateways to secure your private cloud networks
•	Use different VPC for your dev, staging and production environments.
•	Or one VPC with separate subnets for each environment.
•	Use security groups and network ACLs to add extra layer of security to your network.
•	Amazon recommends using security groups to whitelist the traffic and Network ACL’s to blacklist the traffic.
•	It is recommended to create tier-based security groups. Like having db tier in particular security group and web server is different tier. This increases infrastructure security.
•	The naming convention of the security groups also a good way to understand the vpc and its related components.
•	Use different availability zones in VPC to make the application highly available.

# Reference

https://www.youtube.com/watch?v=fpxDGU2KdkA
