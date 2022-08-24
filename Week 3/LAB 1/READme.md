Working with IAM management console

Tasks

1. Login to your root account
I logged into my root account from the amazon login page

2. Create an IAM group with S3 read only acess (S3 support).
I created an IAM group "S3 SUPPORT" from the IAM service

3. Create an IAM group with EC2 read only acess (EC2 support)
I created an IAM group "EC2 SUPPORT" from the IAM service

4. Create an IAM group with EC2 full access (EC2 admin)
I created an IAM group "EC2 ADMIN" from the IAM service

5. Create 3 IAM users and add to the each group above as descibe below:


user      group          permissions
user1     EC2 support     Read-Only access to Amazon EC2
user2     S3 support      Read-Only access to Amazon S3
user3     EC2 admin       Full access to Amazon EC2 instances

I then created 3 IAM user using the IAM service; user1, user2, user3 then added a permission of the group created above. 

6. Test your design
I tested the by logging into each of the IAM user

7. Perform clean up operations
I deleted the users and adjusted the group permission for the next tasks


Replicate the process above for  Schulltech organization descrcibed below:


user               group                       permissions
adminstaff         EC2 support          Read-Only access to Amazon EC2
Techstaff          S3 support           Full access to S3
ITexpert           EC2/SDK admin        full access to EC2 and SDK
financialmanager   billingcontrol       Billing Full Access  
financeuser        billinguser          Billing view access

I created the user "adminstaff and added the permission of EC2 support group
I created the user "Techstaff" and added the permission of S3 support group
I created the user "ITexpert" and added the permission of EC2/SDK admin group
I created the user "financialmanager" and added the permission of billingcontrol group
I created the user "financeuser" and added the permission of billinguser group


NB: I created all the user group first before adding various user to the group created.




https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_users-self-manage-mfa-and-creds.html


