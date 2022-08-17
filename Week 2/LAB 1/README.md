This  task will get you acquainted on how to deploy VPC 


Task 1: Deploy VPC using Management console
1. Launch the AWS Management Console

I lauched the AWS Management Console from the navigation bar

2. Launch a VPC with one public and one private subnets.

I lauched a VPC from the service menu and created two subnets
![VPC CREATED](Image/vpc%20created.jpg)

![PUBLIC$PRIVATE SUBNET](Image/public%20and%20private%20subnet.jpg)

3. Create two route table and associate each one to each subnets

I created two route table from the vpc menu and associated it with each of the subnets
![RT CREATED](Image/public%20rt%20created.jpg)

![PUBLIC SUBNET RT](Image/public%20subnet%20rt.jpg)

![PRIVATE SUBNET RT](Image/private%20subnet%20rt.jpg)

4. Attach an internet gateway to the VPC and a NAT gateway to the private subnet.

I created an internet gateway, then attacched it to the VPC, then i also attached the NAT gateway to the private subnet i created 
![IG to VPC](Image/IG%20to%20VPC.jpg)
![NAT CREATED](Image/NAT%20created.jpg)
![NAT to PRIVATE SUBNET](Image/NAT%20to%20private%20subnet.jpg)

5. Lauch a Linux instance into this VPC and attach the subnet

I lauched a linux instance from the management console into the VPC, attached to the private subnet.
![INSTANCE CRETAED](Image/Instance%20created.jpg)
 
6. Test the network connectivity

I tested the network connectivity using the EC2 instance connect
![TEST CONNECTIVITY](Image/Connectivity%20Testing.jpg)

7. Perform clean up actions
I terminatted the instance and deleted the NAT gateway.







For guide, you are check the links below:

https://docs.aws.amazon.com/cli/latest/reference/ec2/

https://docs.aws.amazon.com/cli/latest/reference/ec2/describe-vpcs.html

