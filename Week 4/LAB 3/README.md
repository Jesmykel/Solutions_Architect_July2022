# Working with placement Groups using AWS CLI

Tasks:
1. Create a placement group
To create a placement group;

In the navigation panel, I chose Placement Groups, Create placement group.
I specified a name for the group. (JesmykelGroup)
I choose the placement strategy for the group. (Cluster)
I didn't choose any tag.
I then chose create group.

![CREATE PG](Images/create%20PG.jpg)

![PG CREATED](Images/PG%20created.jpg)

2. Tag a placement group
To tag a placement group;

In the navigation panel, I chose Placement Groups.
Selected a placement group, and then chose Actions, Manage tags.
I did the following to add tag:
To add a tag, I chose Add tag, and then enter the tag key and value. 
Then choose Save changes.

![TAG PG](Images/Tag%20added.jpg)

3. Launch instances in a placement group
To launch instances in a placement group;

From the EC2 console dashboard, in the Launch instance box, I chose Launch instance.
And then chose From the EC2 console dashboard, in the Launch instance box, choose Launch instance 
Then chose Launch instance from the options that appear. I completed the form as directed, taking care to do the following:
Under Instance type, I selected an instance type that can be launched into a placement group.(c4 micro)
In the Summary box, under Number of instances, I entered the total number of instances (5) that I need in this placement group.
Under Advanced details, for Placement group name, I chose to add the instances to the placement group I created initially. 
I then finally launched the instances.

![LAUNCH INSTANCE](Images/Instance%20launched.jpg)

4. Describe instances in a placement group
To describe the instance type;

In the navigation pane, choose Instances.
I selected the instance I want to describe the placement group.
On the Details tab, under Host and placement group, I found Placement group.

![DESCRIBE INSTANCE](Images/describe%20instance.jpg)

5. Change the placement group for an instance
To change the placement group for an instance;


I firstly created a new placement group as described task (1) above

![CREATE NEW PG](Images/new%20placement%20group%20created.jpg)

I stopped the instance i want to change its placement group using the stop-instances command.

Using the AWS CLI
I used the modify-instance-placement code input and specify the name of the placement group to which to move the instance.

aws ec2 modify-instance-placement --instance-id i-0056cd8339bef8ecc --group-name NewPlacementGroup

I started the instance using the start-instances command.



6. Delete a placement group
To delete the placement group;

I firstly detach the instance in the placement group

Then using the AWS CLI
I used the delete-placement-group code input and specify the placement group name to delete the placement group.

aws ec2 delete-placement-group --group-name JesmykelGroup
aws ec2 delete-placement-group --group-name NewPlacementGroup

![DELETE PG](Images/delete%20placement%20group.jpg)


 


Guide:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html#using-placement-groups
