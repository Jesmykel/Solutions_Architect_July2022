# Working with Elastic Load balancing


1. Create an Application Load Balancer

To create your first load balancer, I completed the following steps.

Prior to the stpes followed below, I created a vpc, with two public subnet in different avalability zone and launched an instance in this subnets.

To create an Application load balancer, I use the code input

aws elbv2 create-load-balancer --name ALB --subnets subnet-00ee97eda93ea291e subnet-061f6de81aeed58bf --security-groups sg-020930699674e26b5

I used the create-target-group command to create a target group, specifying the same VPC that I used for my EC2 instances.

aws elbv2 create-target-group --name ALBTG --protocol HTTP --port 80 --vpc-id vpc-05c1bfd6f69ff4740

aws elbv2 register-targets --target-group-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:targetgroup/ALBTG/3283f2d1ac65e807 --targets Id=i-02733af5d107cc2b2 Id=i-04688c1bdb7f7f4e9	

I used the create-listener command to create a listener for the load balancer with a default rule that forwards requests to the target group:

aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:loadbalancer/app/ALB/8d0026c3a4567797 --protocol HTTP --port 80 --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:us-east-1:930031523124:targetgroup/ALBTG/3283f2d1ac65e807	

To Delete your load balancer

aws elbv2 delete-load-balancer --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:loadbalancer/app/ALB/8d0026c3a4567797
aws elbv2 delete-target-group --target-group-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:targetgroup/ALBTG/3283f2d1ac65e807	


2. Create a Network Load Balancer

To create a IPv4 Network load balancer

I Used the create-load-balancer command to create an IPv4 load balancer.
 
aws elbv2 create-load-balancer --name NLB --type network --subnets subnet-061f6de81aeed58bf subnet-00ee97eda93ea291e 

I Used the create-target-group command to create an IPv4 target group.

aws elbv2 create-target-group --name NLBTG --protocol TCP --port 80 --vpc-id vpc-05c1bfd6f69ff4740

I Used the register-targets command to register instances with your target group:

aws elbv2 register-targets --target-group-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:targetgroup/NLBTG/911a4f78c98e5586 --targets Id=i-09c557a5ffc03c7b7 Id=i-03c65b2e0d2d558e6

I Use the create-listener command to create a listener for load balancer with a default rule that forwards requests to the target group:

aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:loadbalancer/net/NLB/5d2e309861502a34 --protocol TCP --port 80 --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:us-east-1:930031523124:targetgroup/NLBTG/911a4f78c98e5586

To Delete load balancer

I Used the delete command to delete load balancer and target group

aws elbv2 delete-load-balancer --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:loadbalancer/net/NLB/5d2e309861502a34
aws elbv2 delete-target-group --target-group-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:targetgroup/NLBTG/911a4f78c98e5586




3. Create a Gateway Load Balancer

To create a Gateway Load Balancer and register targets

I Used the create-load-balancer command to create a load balancer of type gateway. 

aws elbv2 create-load-balancer --name GLB --type gateway --subnets subnet-00ee97eda93ea291e subnet-061f6de81aeed58bf 

I Used the create-target-group command to create a target group, specifying the service provider VPC in which launched instances.

aws elbv2 create-target-group --name GLBTG --protocol GENEVE --port 6081 --vpc-id vpc-05c1bfd6f69ff4740

I Used the register-targets command to register instances with your target group.

aws elbv2 register-targets --target-group-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:targetgroup/GLBTG/0093a2fe17e11eec2a --targets Id=i-066f29230c2715908 Id=i-07ce0017e542ca9be

I Used the create-listener command to create a listener for the load balancer with a default rule that forwards requests to target group.

aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1:930031523124:loadbalancer/gwy/GLB/eafb8af4c09d8384 --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:us-east-1:930031523124:targetgroup/GLBTG/0093a2fe17e11eec2a


Step 2: To Create a Gateway Load Balancer endpoint

To create a Gateway Load Balancer endpoint

I Used the create-vpc-endpoint-service-configuration command to create an endpoint service configuration using the Gateway Load Balancer.

aws ec2 create-vpc-endpoint-service-configuration --gateway-load-balancer-arns arn:aws:elasticloadbalancing:us-east-1:930031523124:loadbalancer/gwy/GLB/eafb8af4c09d8384 --no-acceptance-required

I Used the modify-vpc-endpoint-service-permissions command to allow service consumers to create an endpoint to service.

aws ec2 modify-vpc-endpoint-service-permissions --service-id vpce-svc-0c1c1b7a18c28dca9 --add-allowed-principals arn:aws:iam::930031523124:root

I Used the create-vpc-endpoint command to create the Gateway Load Balancer endpoint for service of each subnet

aws ec2 create-vpc-endpoint --vpc-endpoint-type GatewayLoadBalancer --service-name com.amazonaws.vpce.us-east-1.vpce-svc-0c1c1b7a18c28dca9 --vpc-id vpc-05c1bfd6f69ff4740 --subnet-ids subnet-00ee97eda93ea291e 
aws ec2 create-vpc-endpoint --vpc-endpoint-type GatewayLoadBalancer --service-name com.amazonaws.vpce.us-east-1.vpce-svc-0c1c1b7a18c28dca9 --vpc-id vpc-05c1bfd6f69ff4740 --subnet-ids subnet-061f6de81aeed58bf 


Step 3: To Configure routing

To configure routing

I firstly created a route-tables (ART, LRT, EPRT)

I Used the create-route command to add an entry to the route table for the internet gateway that routes traffic that's destined for the application servers to the Gateway Load Balancer endpoint.

aws ec2 create-route --route-table-id rtb-092c97826761c1908 --destination-cidr-block 10.0.1.0/24 --vpc-endpoint-id vpce-0159ee78cec64c2dc
aws ec2 create-route --route-table-id rtb-092c97826761c1908 --destination-cidr-block 10.0.1.0/16 --vpc-endpoint-id vpce-0b65a6dc6b27ebde0


I Used the create-route command to add an entry to the route table for the subnet with the application servers that routes all traffic from the application servers to the Gateway Load Balancer endpoint.

aws ec2 create-route --route-table-id rtb-01e7975eb9f2efee8 --destination-cidr-block 0.0.0.0/0 --vpc-endpoint-id vpce-0159ee78cec64c2dc
aws ec2 create-route --route-table-id rtb-01e7975eb9f2efee8 --destination-cidr-block 0.0.0.0/16 --vpc-endpoint-id vpce-0b65a6dc6b27ebde0

I Used the create-route command to add an entry to the route table for the subnet with the Gateway Load Balancer endpoint that routes all traffic that originated from the application servers to the internet gateway.

aws ec2 create-route --route-table-id rtb-0536be44244a90ed3 --destination-cidr-block 0.0.0.0/0 --gateway-id igw-02501b6aee9069e79


4. Create a Classic Load Balancer

On the navigation bar, I chose a Region for thre load balancer. 

On the navigation pane, under LOAD BALANCING, I chose Load Balancers.
I chose Create Load Balancer.
For Classic Load Balancer, I chose Create.

Step 2: To Define load balancer

To define load balancer and listener

For Load Balancer name, I typed a name for the load balancer. (CLB)
For Create LB inside, I selected the same network that I selected for the instances: specific VPC.
I selected a default VPC and choose the subnets for the load balancer, I selected Enable advanced VPC configuration.
I Left the default listener configuration.


Define load balancer
					
[EC2-VPC] For Available subnets, I selected a public subnet using its add icon. The subnet is moved under Selected subnets.


Select Subnets
						
I Chose Next: Assign Security Groups.


Step 3: To Assign security groups to load balancer in a VPC

To assign security group to load balancer


On the Assign Security Groups page, I selected Create a new security group.

Typed a name and description for the security group, left the default name and description. 
							

Select security groups
						
Choose Next: Configure Security Settings.

Choose Next: Configure Health Check to continue to the next step.

Step 4: Configure health checks for your EC2 instances
Elastic Load Balancing automatically checks the health of the EC2 instances for your load balancer. 

To configure health checks for your instances

On the Configure Health Check page, I left Ping Protocol set to HTTP and Ping Port set to 80.
For Ping Path, I replaced the default value with a single forward slash ("/"). 


Configure Health Check
						
For Advanced Details, I left the default values.
Chose Next: Add EC2 Instances.

Step 5: Register EC2 instances with load balancer

To register EC2 instances with load balancer

On the Add EC2 Instances page, I selected the instances to register with load balancer.
Leaving cross-zone load balancing and connection draining enabled.
I Chose Next: Add Tags.
I Selected running instances after I created the load balancer
I Set up Auto Scaling to register the instances automatically when it launches them. 

Step 6: To Tag load balancer (optional)

I didn't add any tags to load balancer
I then, chose Review and Create.

Step 7: To Create and verify  load balancer

To create and testload balancer

On the Review page, I chose Create.

After notified that load balancer was created, I chose Close.

I selected the new load balancer.

On the Description tab, check the Status row. 
After at least one of the EC2 instances is in service, I tested load balancer. Copy the string from DNS name and pasted it into the address field of an internet-connected web browser.

Step 8: To Delete load balancer

To delete load balancer


On the navigation pane, under Load Balancing, choose Load Balancers.

I Selected the load balancer.
Chose Actions, Delete.
When prompted for confirmation, I chose Yes, Delete.


5. Perform clean up operations

Most of the clean operations were created alongside the steps above to minimize cost incurred.





NB: You need to launch at least two instances to do this. 

Guide
https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/load-balancer-getting-started.html

