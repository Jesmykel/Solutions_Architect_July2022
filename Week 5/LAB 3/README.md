# Working with EFS

Task

1. Create your Amazon EC2 resources and launch two EC2 instance.
I launched two instances in the EC2 resources using the AWS management console

2. Create your Amazon EFS file system with One Zone storage.

I Choose Create file system to open the Create file system dialog box.
I Entered a Name for the file system.
For Virtual Private Cloud (VPC), I kept it set to default VPC.
For Availability and Durability, I choose One Zone to create a file system that uses One Zone storage classes. 
I choose the Availability Zone that I want the file system created in.
I Chose Create to create a file system that uses the following service recommended settings:
Automatic backups turned on. 
Mount targets 
General Purpose performance mode 
Bursting throughput mode 
Encryption of data at rest enabled using your default key for Amazon EFS (aws/elasticfilesystem) 
Lifecycle Management 
Transition into IA set to 30 days since last access
Transition out of IA set to On first access
I then selected next
I left the security settings as default
Then selected next
Then finally choose create.

3. Connect to each of your Amazon EC2 instances, and mount the Amazon EFS file system using the same mount target for each instance.
I connect to the ec2 instance i created in task 1 using the Ec2 instance connect
I used the command line to mount the EFS file system

sudo yum install -y amazon-efs-utils
mkdir efs
After which i edited the inbound security rule to allow port nfs port 2048
Then the command line

sudo mount -t efs -o tls fs-00f2a6d669fd4b8a6:/ efs (from the EFS file initially created)
cd efs
ll
sudo echo hello-world.txt

I repeated the process for the both instance after which I performed a clean operation.










Guide:
https://docs.aws.amazon.com/efs/latest/ug/gs-step-two-create-efs-resources.html
