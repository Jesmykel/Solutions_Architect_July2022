# Working with Elastic Load balancing


1. Create an Application Load Balancer

To create your first load balancer, complete the following steps.

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

In the navigation pane, under Load Balancing, I choose Target Groups.
I Choose Create target group.
I kept Target type as instance.
For Target group name, I entered a name for the new target group.
I kept Protocol as TCP, and Port as 80.
I selected the VPC containing the instances. Keep the protocol version as HTTP1.
For Health checks, I kept the default settings.
Then, chose Next.

On the Register targets page, I completed the following steps. 

For Available instances, I select two instances.
I kept the default port 80, and choose Include as pending below.
I chose Create target group.

Step 2: To choose a load balancer type
Elastic Load Balancing supports different types of load balancers. 
To create a Network Load Balancer

On the navigation bar, I chose a Region for load balancer. I choose the same Region that I used for the EC2 instances.
In the navigation pane, under Load Balancing, I chose Load Balancers.
I chose Create Load Balancer.

For Network Load Balancer, I chose Create.

Step 3: To configure load balancer and listener
To create a Network Load Balancer.

To configure load balancer and listener

For Load balancer name, I entered a name for the load balancer. (NLB) 
For Scheme and IP address type, I kept the default values.
For Network mapping, I selected the VPC that was used for your EC2 instances. For each Availability Zone that I used to launch the EC2 instances, I selected the Availability Zone and then selected one public subnet for that Availability Zone.
For Listeners and routing, I kept the default protocol and port, and selected the target group from the list. 
For Default action, I selected the target group that I created and registered in step 1.
I didn't add tag to categorize your load balancer. 
I Reviewed configuration, and choose Create load balancer. 

Step 4:To Test load balancer
After creating the load balancer.

To test load balancer

After I was notified that load balancer was created successfully, I chose Close.
In the navigation pane, under Load Balancing, I chose Target Groups.
I Selected the newly created target group.
Chose Targets and verify that instances are ready. 
In the navigation pane, under Load Balancing, choose Load Balancers.
I selected the newly created load balancer.
I chose Description and copy the DNS name of the load balancer (http://nlb-b62036ee9bace058.elb.us-east-1.amazonaws.com/). I Pasteed the DNS name into the address field of an internet-connected web browser. 

Step 5: To Delete load balancer

To delete load balancer

In the navigation pane, under Load Balancing, choose Load Balancers.
I selected the load balancer and I chose Actions, Delete.
When prompted for confirmation, I chose Yes, Delete.




3. Create a Gateway Load Balancer

On the navigation pane, under Load Balancing, I chose Target Groups.
For Chose a target type.
For Target group name, I entered a name for the target group.(GLBTG)
The Protocol is GENEVE, and Port is 6081.
For VPC, I selected a virtual private cloud (VPC) with the instances that I want to include in the target group.
For Health checks, I modified the health check settings as needed.
I didn't add Tags.
Then, Choose Next.

I Added two targets as follows:

I selected two instances, entered two ports, and then chose Include as pending below.
Chose Create target group.

To create a Gateway Load Balancer

In the navigation pane, under Load Balancing, I chose Load Balancers.
I Chose Create Load Balancer.
Under Gateway Load Balancer, I chose Create.
For Load balancer name, I entered a name for the load balancer. (GLB)
For IP address type, I chose IPv4.
For VPC, I selected the service provider VPC.
For Mappings, I selected all of the Availability Zones in which I launched the instances, and the corresponding public subnets.
For Default action, I selected a target group to forward traffic to.
I didn't add Tags
I reviewed configuration, and I chose Create load balancer.

Step 2:  To Create a Gateway Load Balancer endpoint

To create a Gateway Load Balancer endpoint

In the navigation pane, I chose Endpoint Services.
I chose Create Endpoint Service and do the following:
For Associate Load Balancers, I selected the Gateway Load Balancer.
For Require acceptance for endpoint, I selected Acceptance required to accept connection requests to your service manually. 
I didn't add any tag. 
I Chose Create service. I Choose the service ID. Saveed the service name from the Details tab.
I Chose Actions, Add principals to whitelist. I Entered the ARNs of the service consumers that are allowed to create an endpoint to the service.

In the navigation pane, I chose Endpoints.
I Chose Create Endpoint and did the following:

For Service category, I chose Find service by name.
For Service name, I enter the service name that I saved earlier, and then chose Verify.
For VPC, I selected the service consumer VPC.
For Subnets, I selected a subnet for the Gateway Load Balancer endpoint.
I didn't add tag.
I then, Chose Create endpoint. The initial status is pending acceptance.

Step 3: To Configure routing

To configure routing

In the navigation pane, I chose Route Tables.
I Selected the route table for the internet gateway and did the following:

Chose Actions, I Edited routes.
Chose Add route. For Destination, I enter the CIDR block of the subnet for the application servers. For Target, select the VPC endpoint.(Instance)
Choose Save routes.

Selected the route table for the subnet with the application servers and did the following:

Chose Actions, Edit routes.
Chose Add route. For Destination, enter 0.0.0.0/0. For Target, select the VPC endpoint. (Instance)
Chose Save routes.

Selected the route table for the subnet with the Gateway Load Balancer endpoint, and did the following:

Choose Actions, Edit routes.
Choose Add route. For Destination, enter 0.0.0.0/0. For Target, select the internet gateway.
Choose Save routes.




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

Step 8: TO Delete load balancer

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

