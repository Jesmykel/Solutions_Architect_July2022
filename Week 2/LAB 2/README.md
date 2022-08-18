Task: Create a nondefault VPC using AWS CLI

1. Open your CLI and run a configuration setting
I opened my CLI from the management console after logging in to my AWS account

2. Lauch a VPC
I lauched a VPC using the code input
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query Vpc.VpcId --output text 

![create VPC](Images/create%20vpc.jpg)

3. Create two subnets (a public and a private subnet)
I created two subnets using the code input
aws ec2 create-subnet --vpc-id vpc-061c9afd702448dcf --cidr-block 10.0.1.0/24
and
aws ec2 create-subnet --vpc-id vpc-061c9afd702448dcf --cidr-block 10.0.1.0/24

![CREATE SUBNET](Images/subnet%201.jpg)
![CREATE SUBNET](Images/subnet%202.jpg)


4. Make your subnet public by creating and attaching an internet gateway
To make one of my subnet public;

I created an internet gateway using the code input
aws ec2 create-internet-gateway --query InternetGateway.InternetGatewayId --output text

I attached the gateway to a VPC using the code input
aws ec2 attach-internet-gateway --vpc-id vpc-061c9afd702448dcf --internet-gateway-id igw-0588e4224e585d120

![ATTACH GATEWAY](Images/Attach%20gateway.jpg)

I created a route-table in my VPC using the code input
aws ec2 create-route-table --vpc-id vpc-061c9afd702448dcf --query RouteTable.RouteTableId --output text

I created a route in the route-table that point all traffic to the IGW using the code input
aws ec2 create-route --route-table-id rtb-0c01864b40e27889a --destination-cidr-block 0.0.0.0/0 --gateway-id igw-0588e4224e585d120

I then associated route-table to one of my subnet to make the subnet public using the code input
aws ec2 associate-route-table  --subnet-id subnet-0dc4f392808b35e6d --route-table-id rtb-0c01864b40e27889a

![ASSOCIATE RT](Images/Associate%20RT.jpg)

I then modified the public IP addressing behavior of the subnet so that an instance launched into the subnet automatically receives a public IP address using the code input
aws ec2 modify-subnet-attribute --subnet-id subnet-0dc4f392808b35e6d --map-public-ip-on-launch

5. Create a security group and add a SSH access from anywhere
I created a security group and added an SSH access from anywhere using the code input
aws ec2 create-security-group --group-name SSHAccess --description "Security group for SSH access" --vpc-id vpc-061c9afd702448dcf
and
aws ec2 authorize-security-group-ingress --group-id sg-0a2687d28166b4917 --protocol tcp --port 22 --cidr 0.0.0.0/0

1[SG](Images/Security%20group.jpg)
![SSH AUTO](Images/SSH%20authorization.jpg)

6. Lauch an instance into your subnet 
I lauched an instance using the code input
aws ec2 run-instances --image-id ami-0cabc39acf991f4f1 --count 1 --instance-type t2.micro --key-name jesmykel --security-group-ids sg-0a2687d28166b4917 --subnet-id subnet-0dc4f392808b35e6d

![LAUNCH INSTANCE](Images/create%20instance.jpg)

I checked the state of the instance using the code input
aws ec2 describe-instances --instance-id i-009c455919740e8b9 --query "Reservations[*].Instances[*].{State:State.Name,Address:PublicIpAddress}"

![INSTANCE STATE](Images/instance%20state.jpg)

I connected the instance from the managemant console using the EC2 instance connect and i was granted access.

![INSTANCE CONNECT](Images/instance%20connect.jpg)

7. Clean Up
I performed clean up operation by 
terminating the instance, deleting the SG, deleting the subnets, deleting route table, detaching the IGW from VPC, deleting the IGW, deleting VPC

![CLEAN UP](Images/clean%20up.jpg)




https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-commands-example.html

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-commands-example-ipv6.html

https://docs.aws.amazon.com/vpc/index.html
