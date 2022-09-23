# Working with Elastic Beanstalk

1. To Create an example application

I Opened the Elastic Beanstalk console 
For Platform, I chose a platform, and then chose Create application.

To run the example application on AWS resources, Elastic Beanstalk takes the following actions. They took about five minutes to complete.

Creates an Elastic Beanstalk application named myfirstapp.
Launches an environment named Myfirstapp-env with these AWS resources:
An Amazon Elastic Compute Cloud (Amazon EC2) instance (virtual machine)
An Amazon EC2 security group
An Amazon Simple Storage Service (Amazon S3) bucket
Amazon CloudWatch alarms
An AWS CloudFormation stack
A domain name
Creates a new application version named Sample Application. 
Deploys the code for the example application to the Myfirstapp-env environment.



2. Explore your environment

I Opened the Elastic Beanstalk console. 
In the navigation panel, I choose Environments, and then choose the name of environment from the list.

The environment overview panel shows top level information about your environment. This includes name, URL, current health status, the name of the currently deployed application version, and the platform version that the application is running on.


3. Deploy a new version of your application

I Downloaded the sample application that matches my environment's platform.

.NET – dotnet-asp-v1.zip

I Opened the Elastic Beanstalk console. 
In the navigation panel, chose Environments, and then chose the name of my environment from the list.

On the environment overview page, I chose Upload and deploy.
Chose file, and then upload the sample application source bundle that I downloaded.


To Upload and deploy dialog.
          
The console automatically fills in the Version label with a new unique label. 
I Chose Deploy.


4. Configure your environment

In the navigation panel, I chose Configuration.
In the Capacity configuration category, I chose Edit.
In the Auto Scaling group section, I change Environment type to Load balanced.
In the Instances row, I changed Max to 4, and then changed Min to 2.

Then, Chose Apply.

A warning tells me that this update replaces all of my current instances. I Chose Confirm.
In the navigation panel, I chose Events.
I Verified the configuration change
When the environment update is complete and the environment is ready, I verified change.

To verify the increased capacity

In the navigation panel, I chose Health.
Looked at the Enhanced health overview page.


5. Clean up

To Delete all application versions.

In the navigation panel, I choose Applications, and then chose myfirstapp.
In the navigation panel, I find the application's name and chose Application versions.
On the Application versions page, I selected application versions that I want to delete.
Chose Actions, and then chose Delete.
Turned on Delete versions from Amazon S3.
Chose Delete, and then chose Done.

To Terminate the environment.

In the navigation panel, I chose myfirstapp, and then chose Myfirstapp-env in the environment list.
Chose Environment actions, and then chose Terminate Environment.
I Confirmed that I want to terminate Myfirstapp-env by typing the environment name, and then chose Terminate.

To Delete the myfirstapp application.

In the navigation pane, I chose the myfirstapp.
Chose Actions, and then chose Delete application.

I Confirm that I want to delete myfirstapp by typing the application name, and then choose Delete.



Guide:

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/GettingStarted.html

