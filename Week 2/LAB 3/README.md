Task :  Create a dual Stack VPC and subnets using AWS CLI

Step:
1. Launch a non-default VPC
I created a VPC with a 10.0.0.0/16 CIDR block and associate an IPv6 CIDR block with the VPC using the code input;
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --amazon-provided-ipv6-cidr-block
aws ec2 describe-vpcs --vpc-id vpc-0250257399aae3c44

2. Create two subnets
I created two subnets using the code inputs;
aws ec2 create-subnet --vpc-id vpc-0250257399aae3c44 --cidr-block 10.0.0.0/24 --ipv6-cidr-block 2600:1f18:1b73:9c00::/56
aws ec2 create-subnet --vpc-id vpc-0250257399aae3c44 --cidr-block 10.0.1.0/24 --ipv6-cidr-block 2600:1f18:1b73:9c01::/56
 
3. Create an internet gateway to one of the subnets with route table 
I created an internet gateway using the code inputs;
aws ec2 create-internet-gateway
aws ec2 attach-internet-gateway --vpc-id vpc-0250257399aae3c44 --internet-gateway-id igw-0642f432d670f016b
aws ec2 create-route-table --vpc-id vpc-0250257399aae3c44
aws ec2 create-route --route-table-id rtb-0c7c7892f49839afc --destination-ipv6-cidr-block ::/0 --gateway-id igw-0642f432d670f016b
aws ec2 associate-route-table  --subnet-id subnet-078ad48dae81488b4 --route-table-id rtb-0c7c7892f49839afc

4. Configure an egress-only private subnet
I configured an egress-only private subnet using the code inputs;
aws ec2 create-egress-only-internet-gateway --vpc-id vpc-0250257399aae3c44
aws ec2 create-route-table --vpc-id vpc-0250257399aae3c44
aws ec2 create-route --route-table-id rtb-05c720b1c9777c7c8 --destination-ipv6-cidr-block ::/0 --egress-only-internet-gateway-id eigw-0657bc4ae6caede7d
aws ec2 associate-route-table --subnet-id subnet-04d3b086c5afe5535 --route-table-id rtb-05c720b1c9777c7c8

5. Modify the IPv6 addressing behavior of the subnets
I modified the IPv6 addressing behavior of the subnets using the code inputs;
aws ec2 modify-subnet-attribute --subnet-id subnet-078ad48dae81488b4 --assign-ipv6-address-on-creation
aws ec2 modify-subnet-attribute --subnet-id subnet-04d3b086c5afe5535 --assign-ipv6-address-on-creation

6. Lauch an instance into your public subnet
I lauched an instance into the public subnet using the code input;
aws ec2 run-instances --image-id ami-0de53d8956e8dcf80 --count 1 --instance-type t2.micro --key-name jesmykel --security-group-ids sg-0cc6c9bf4276f87eb --subnet-id subnet-078ad48dae81488b4

7. Launch an instance into your private subnet
I launched an instance into the private subnet using the code input;
aws ec2 run-instances --image-id ami-0cabc39acf991f4f1 --count 1 --instance-type t2.micro --key-name jesmykel --security-group-ids sg-097dc1ff4190c2bc3 --subnet-id subnet-04d3b086c5afe5535


8. Perform clean up operations.
I finally then performed a clean up operation by first terminatting the instance and using the code input;
aws ec2 delete-security-group --group-id sg-0cc6c9bf4276f87eb
aws ec2 delete-security-group --group-id sg-097dc1ff4190c2bc3
aws ec2 delete-subnet --subnet-id subnet-078ad48dae81488b4
aws ec2 delete-subnet --subnet-id subnet-04d3b086c5afe5535
aws ec2 delete-route-table --route-table-id rtb-0c7c7892f49839afc
aws ec2 delete-route-table --route-table-id rtb-05c720b1c9777c7c8
aws ec2 detach-internet-gateway --internet-gateway-id igw-0642f432d670f016b --vpc-id vpc-0250257399aae3c44
aws ec2 delete-internet-gateway --internet-gateway-id igw-0642f432d670f016b
aws ec2 delete-egress-only-internet-gateway  --egress-only-internet-gateway-id eigw-0657bc4ae6caede7d
aws ec2 delete-vpc --vpc-id vpc-0250257399aae3c44


 


https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-commands-example.html

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-commands-example-ipv6.html

https://docs.aws.amazon.com/vpc/index.html
