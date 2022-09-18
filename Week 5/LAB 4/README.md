# Working with Auto scaling groups

Tasks:

1. To Create a launch template

I opened the Launch templates page of the Amazon EC2 console.
On the navigation bar at the top of the screen, I selected an AWS Region. 
Choose Create launch template.
For Launch template name, I entered a name
Under Auto Scaling guidance, I selected the check box.
For Application and OS Images (Amazon Machine Image), I chose a version of Amazon Linux 2 (HVM) from the Quick Start list. 
For Instance type, I chose a hardware configuration that is compatible with the AMI that was specified.
For Key pair (login), I chose an existing key pair. 
For Network settings, Security groups, I chose a security group in the same VPC that I plan to use as the VPC for Auto Scaling group. 
I then Choose Create launch template.
On the confirmation page, I chose Create Auto Scaling group.


2. To Create a single-instance Auto Scaling group

On the Choose launch template or configuration page, for Auto Scaling group name, I entered a name.
Then Chose Next.
The Choose instance launch options page appears
In the Network section, I selected my preffered VPC. 
For Availability Zones and subnets, I chose a subnet from each Availability Zone. 
[Launch template only] In the Instance type requirements section, I used the default setting to simplify this step. 
Keep the rest of the defaults for this tutorial and choose Skip to review.
On the Review page, I reviewed the information for the group, and then chose Create Auto Scaling group.


3. To Verify your Auto Scaling group

I Opened the Auto Scaling groups page of the Amazon EC2 console.
I Selected the check box next to the Auto Scaling group that I created.
A split pane opens up in the bottom of the Auto Scaling groups page. 
I Chose the second tab, Activity. Under Activity history, I viewed the progress of activities that are associated with the Auto Scaling group. 
On the Instance management tab, under Instances, I viewed the status of the instance.
I verified that your instance launched successfully.


4. To Terminate an instance in your Auto Scaling group

I Opened the Auto Scaling groups page of the Amazon EC2 console.
Selected the check box next to your Auto Scaling group.
On the Instance management tab, under Instances, I selected the ID of the instance.
This takes me to the Instances page of the Amazon EC2 console, where I can terminate the instance.
Chose Actions, Instance State, Terminate. When prompted for confirmation, I chose Yes, Terminate.
On the navigation pane, under Auto Scaling, chose Auto Scaling Groups. Selected Auto Scaling group and chose the Activity tab.
On the navigation pane, under Instances, choose Instances. This page shows both the terminated instance and the new running instance.


5. To Clean up

Open the Auto Scaling groups page of the Amazon EC2 console.
Select your Auto Scaling group.
I Chose Delete. When prompted for confirmation, I chose Delete.
A loading icon in the Name column indicates that the Auto Scaling group is being deleted. 

To delete your launch template

Open the Launch templates page of the Amazon EC2 console.
Selected the launch template.
Chose Actions, Delete template. When prompted for confirmation, I chose Delete launch template.





Guide:
https://docs.aws.amazon.com/autoscaling/ec2/userguide/GettingStartedTutorial.html
