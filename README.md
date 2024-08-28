CONFIGURATION MANAGEMENT USING ANSIBLE
======================================

ARCHITECTURE DIAGRAM: 

![AWS_LIGHT](https://github.com/user-attachments/assets/4b189567-54a4-4ae5-88a9-a55b25993353)


Deploying a complete application stack using Ansible configuration management.

Description : 
I've used ansible to deploy a complete application stack on AWS cloud using Ansible , a configuration management tool.
This was completed in 3 phases.
Application name: Vprofile



Phase 1 : 
---------

The first phase was used to create a cloud architecture for the application using AWS .

Components : 

VPC
Subnets (public & private)
Internet gateway
Route Tables (public & private)
NAT gateway
Bastion Host.
Security Groups
Key pair
EC2

Playbooks were created with variable and modules specified  for launching the VPC and its components as listed above.
Python BOTO was used to make API calls by using IAM roles.
VPC was created in 3 Zones (NOTE: the diagram shows 2 zones)
Bastion host was created in the public subnet.
Ran the playbooks to launch the VPC and its components using the ansible controller.
The EC2 for the ansible controller was launched in the default VPC.



Phase 2: 
--------

Phase 2 was used to setup the infrastructure for  application stack in the VPC.
I automated the infrastructure for the application stack using ansible playbooks and launched it in the VPC that was created in phase 1.
IAAC.

Components : 
MAVEN
Nginx
Tomcat
MySQL
RabbitMQ
Keypair
Elastic Load balancer (ELB)
Security Group

Playbooks were used along with variables and modules making an API connection to AWS.
ELB was launched as a part of the infrastructure in the private subnet
EC2 instances were launched for each component and placed in the private subnet.
Keypairs were created.
CIDR was specified for the VPC.


Phase 3: 
--------


Phase 3 was used to provision the architecture with services through an SSH.
An inventory  and modules file was used.
Provision Nginx, mysql , rabbit MQ, Tomcat.
Move the ansible control machine to the VPC.
Ansible would SSH into the EC2 instance to configure the OS and install and provision service.
Run Playbook to build code and deploy on Tomcat server, run playbook for web (Nginx), DB (MYsql) , RabbitMQ.
