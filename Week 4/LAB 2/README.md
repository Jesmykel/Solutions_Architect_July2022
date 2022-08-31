#  Working with EBS

Tasks:
1. Create an Amazon EBS volume
To create Amazon EBS volume;

I opened the Amazon EC2 console at https://console.aws.amazon.com/ec2/.
In the navigation pane, I chose Volumes.
I chose Create volume.
For Volume type, I chose the type of volume to create. 
For Size, I entered the size of the volume, in GiB.
For Availability Zone, I chose the Availability Zone in which to create the volume.
I didn't set the encryption status for the volume.
I didn't choose any tag
I finally chose Create volume.

2. Attach and mount your volume to an EC2 instance
To attach and mount volume to an EC2 instance;

In the navigation panel, I chose Volumes.
I selected the volume to attach and choose Actions, Attach volume.
For Instance, I selected the instance from the list of options provided.
For Device name,The block device driver for the instance assigned a device name when mounting the volume.
I chose Attach volume.
I then finally connect to the instance and mounted the volume.

3. Create a snapshot of your volume
To create snapshot of my volume;

In the navigation panel, I chose Snapshots, then create snapshot.
For Resource type, choose Volume.
For Volume ID, I selected the volume from which to create the snapshot.
For Description, I entered a brief description for the snapshot.
I didn't choose any tag.
I then finally chose Create snapshot.

4. Create a new volume from your snapshot
To create new volume from the snapshot i initially created;

In the navigation panel, I chose Volumes.
I chose create volume.
For Volume type, I chose the type of volume to create.
For Size, I entered the size of the volume, in GiB.(100GB) 
For Availability Zone, I chose the Availability Zone in which to create the volume.(us-east 1c)
For Snapshot ID, I selected the snapshot from which to create the volume.
I didn't set any encryption for the volume.
I didn't assign custom tags to the volume
I then finally chose Create Volume.

5. Attach and mount the new volume to your EC2 instance
To attach and mount new volume to EC2 instance;

In the navigation panel, I chose Volumes.
I selected the volume to attach and chose Actions, Attach volume.
For Instance, I selected the instance from the list of options.
For Device name, The block device driver for the instance assigned a device name when mounting the volume.
I choose Attach volume.
I then finally connected to the instance and mounted the volume.





Guide:

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes.html

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-attaching-volume.html
