This  task will get you acquainted on how to deploy VPC 


Task 1: Deploy VPC using Management console
1. Launch the AWS Management Console
I lauched the AWS Management Console from the navigation bar

2. Launch a VPC with one public and one private subnets.
I lauched a VPC from the service menu and created two subnets

3. Create two route table and associate  each one to each subnets
I created two route table from the vpc menu and associated it with each of the subnets

4. Attach an internet gateway to the VPC and a NAT gateway to the private subnet.
I created an internet gateway, then attacched it to the VPC, then i also attached the NAT gateway to the private subnet i created 

5. Lauch a Linux instance into this VPC and attach the subnet
I lauched a linux instance from the management console into the VPC, attached to the private subnet.
 
6. Test the network connectivity
I tested the network connectivity using the EC2 instance connect

7. Perform clean up actions
I terminatted the instance and deleted the NAT gateway.







For guide, you are check the links below:

https://docs.aws.amazon.com/cli/latest/reference/ec2/

https://docs.aws.amazon.com/cli/latest/reference/ec2/describe-vpcs.html

