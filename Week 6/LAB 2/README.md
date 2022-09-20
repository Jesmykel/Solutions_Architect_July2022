#  Working with AWS Cloudtrail

1. Review AWS account activity in event history

I Signed in to the AWS Management Console
Reviewed the information on dashboard about the most recent events that have occurred my AWS account. An example of recent event is ConsoleLogin event, showing that I just signed in to the AWS Management Console.


The CloudTrail dashboard showing recent events
     
To see more information about event, I expanded it.

The CloudTrail dashboard showing expanded information about events
     
In the navigation pane, I choose Event history. I viewed filtered list of events, with the most recent events showing first.
     
I saved event history by downloading it as a file in CSV. 


2. Create your first trail

On the CloudTrail service home page, the Trails page, I chose Create trail.
In Trail name, I gave the trail a name. 
I Left default settings for AWS Organizations organization trails. 
For Storage location, I chose Create new S3 bucket to create a bucket. 

The Create trail page
     
I Cleared the check box to disable Log file SSE-KMS encryption. 
I Left default settings in Additional settings.
For now, I didn't send logs to Amazon CloudWatch Logs.

In Tags, I didn't add 
I chose Next.

On the Choose log events page, I selected event types to log.
I Left default settings for Data events and Insights events. Then, Chose Next.

On the Review and create page, I reviewed the settings I have chosen for trail. 
The Trails page shows my new trail in the table. 


3. View your log files

In the navigation pane, chose Trails. On the Trails page, I find the name of the trail I created.
In the row for the trail, I chose the value for the S3 bucket. 
An Amazon S3 bucket for a trail, showing the structure for log files in AWS Regions.
I Navigateed the bucket folder structure.

 


Guide:
https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-tutorial.html
