# Working with RDS in AWS

Tasks:

1. Create an Amazon VPC for use with a DB instance

In the upper-right corner of the AWS Management Console, I made sure the AWS Region is the same as the one where you created EC2 instance.
In the navigation pane, I chose Databases.
I chose Create database.
On the Create database page, shown following, I made sure that the Standard create option is chosen, and I then chose MySQL.

Under the Select engine Section
                        
In the Templates section, I chose Free tier.
In the Availability and durability section, I kept the defaults.
In the Settings section, I set these values:

DB instance identifier – database-1
Master username – admin
I left the Auto generate a password option turned off.
Master password – set a password.
then Confirmed password – I Retyped the password.

Under the Settings sections
                    
In the Instance configuration section, I set these values:

Burstable classes (includes t classes)
db.t3.micro

Under the Instance configuration section
                            
In the Storage section, I kept the defaults.
In the Connectivity section, I set these values and keep the other values as their defaults:
For Compute resource, I chose Connect to an EC2 compute resource.
For EC2 instance, I created a new EC2 instance and attached the RD to it

Under Connectivity section
                    
In the Database authentication section, make sure Password authentication is selected.
Open the Additional configuration section, and enter sample for Initial database name. Keep the default settings for the other options.
To create your MySQL DB instance, choose Create database.
Your new DB instance appears in the Databases list with the status Creating.

 Create a VPC with private and public subnets and multiple subnets

In the navigation pane, I chose Your VPCs.
I chose Create VPC only 
I added a tag
I added an ipv4 cidr block
Then chose create.

After creating the VPC
In the navigation pane, i chose subnets
I chose create subnet
I entered the required details
I repeated the steps to create a public and private subnet in different Availability zones.

Create a VPC security group for a public web server 

In the navigation pane, I chose Your VPCs.
I chose Security group 
I chose Create Security group
I entered the basic details
Chose the DB-VPC i created
I added inbound rule of port 80 and 443
I didn't add any tag
Then, chose create security group.

Create a VPC security group for a private DB instance

In the navigation pane, I chose Your VPCs.
I chose Security group 
I chose Create Security group
I entered the basic details 
Chose the DB-VPC I created
I added inbound and outbound rule of port 80 and 443
I didn't add any tag
Then, chose create security group.

 Create a DB subnet group

In the navigation pane, I chose Your VPCs.
I chose RDS
I chose subnet group
I chose create db subnet group
I entered the subnet group details
I chose the vpc I created for the db
I chose the subnet I created in the different availability zone.
Then chose create.





Performn Clean up actions subnet, subnet group, security group, DB-VPC, DB instance then finally the instance I created.




NB: If you fail to perform clean up actions, costs are usually incurred.




Guide

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/TUT_WebAppWithRDS.html

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Tutorials.html
