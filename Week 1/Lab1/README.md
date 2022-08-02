This Week lab will focus on getting you acquainted with Amazon S3 using the aws cli

# Task 1: Create a S3 bucket using AWS CLI

1. Lauch AWS cloud shell

I lauched the aws cloud shell from the navigation bar in the IAM user that has a full access

2. Create a S3 bucket

I created a S3 bucket using the code input below

aws s3 mb s3://jesmykel-bucket

![create bucket](Images/create%20bucket.jpg)
 
3. Create a folder in your S3 bucket

I craeted a folder using the code input below after i already uploaded the file in the home directory of my account cloud shell

aws s3 cp ./lab.jpeg s3://jesmykel-bucket/new-folder/lab

![create folder and upload image](Images/create%20folder%20and%20upload%20image.jpg)

4. Upload objects to your S3 bucket

Task was already created in 3 above

5. List the object in your S3 bucket

aws s3 ls s3://jesmykel-bucket

![list object](Images/list%20object.jpg)

6. Download Object from your S3 bucket

aws s3api get-object --bucket jesmykel-bucket --key new-folder/lab labdownload.jpeg --output json

![download object](Images/download%20image.jpg)

7. Delete object in your s3 bucket

aws s3 rm s3://jesmykel-bucket/new-folder/lab 

![delete object](Images/delete%20image.jpg)

8. Delete your S3 bucket

aws s3 rb s3://jesmykel-bucket

![delete bucket](Images/delete%20bucket.jpg)




For guide, kindly visit

https://docs.aws.amazon.com/cli/latest/reference/s3api/create-bucket.html

https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html

https://docs.aws.amazon.com/cli/latest/userguide/cli-services-s3-commands.html
