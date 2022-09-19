# Working with CLoudwatch using AWS Console 

# Monitoring 

1. Enable billing alerts

In the navigation pane, I chose Billing Preferences.
Selected Receive Billing Alerts.
Then, Chose Save preferences.

2. Create a billing alarm

I Opened the CloudWatch console at https://console.aws.amazon.com/cloudwatch/.
In the navigation pane, I chose Alarms, Then Created Alarm.
I Chose Select metric, Billing, Total Estimated Charge.
Selected the checkbox next to EstimatedCharges and choose Select metric
For Whenever my total AWS charges for the month exceed, I specified the monetary amount that must be exceeded to trigger the alarm and send an email notification. Then chose Next.
For send a notification to, do one of the following:
I Chose Create N ew topic and then select the topic to notify under Send a notification to.
Then, Chose Create Alarm.

After which I confirmed from the email address I added


3. Check the alarm status

In the navigation pane, choose Alarms.
I Selected the check box next to the alarm. Until the subscription is confirmed, it was shown as "Pending confirmation". After the subscription is confirmed, I refresh the console to show the updated status.

4. Edit a billing alarm


I Opened the CloudWatch console at https://console.aws.amazon.com/cloudwatch/.
In the navigation pane, I chose Alarms.
Selected the check box next to the alarm and chose Actions, Edit.
For Whenever my total AWS charges for the month exceed, I specified the new amount that must be exceeded to trigger the alarm and send an email notification.
Then, Chose Save Changes.


5. Delete a billing alarm

I Opened the CloudWatch console at https://console.aws.amazon.com/cloudwatch/.
In the navigation pane, I chose Alarms.
Selected the check box next to the alarm and chose Actions, Delete.
When prompted for confirmation, choose Yes, Delete.




# Alarms

1. Create a CPU usage alarm

Open the CloudWatch console at https://console.aws.amazon.com/cloudwatch/.

In the navigation pane, chose Alarms, All Alarms.
Chose Create alarm.
Chose Select metric.
In the All metrics tab, I chose EC2 metrics.
Chose a metric category (Per-Instance Metrics).
Under Specify metric and conditions, for Statistic I choose Average. 
Chose a period of 5 minutes
Under Conditions, I specified the following:
For Threshold type, choose Static.
For Whenever CPU Utilization is, I specified Greater. 
Choose Next.
Under Notification, I chose In alarm and select an SNS topic to notify when the alarm is in ALARM state
To have the alarm send multiple notifications for the same alarm state or for different alarm states, I choose Add notification.
When finished, I chose Next.
I Entered a name and description for the alarm. The name only ASCII characters. Then choose Next.
Under Preview and create, I confirmed that the information and conditions are what I wanted, then chose Create alarm.

2. Create a load balancer latency alarm that sends email

In the navigation pane, I chose Alarms, All Alarms.
Coose Create alarm.
Under CloudWatch Metrics by Category, I chose the ELB Metrics category.
Selected the row with the Classic Load Balancer and the Latency metric.
For the statistic, chose Average, chose one of the predefined percentiles
For the period, chose 1 Minute.
Chose Next.

Under Alarm Threshold, I entered a unique name for the alarm 
Under Whenever, for is, chose > and enter 0.1. For for, I entered 3.
Under Additional settings, for Treat missing data as, I choose ignore (maintain alarm state) so that missing data points don't trigger alarm state changes.
For Percentiles with low samples, choose ignore (maintain the alarm state) so that the alarm evaluates only situations with adequate numbers of data samples.
Under Actions, for Whenever this alarm, choose State is ALARM. For Send notification to, I choose an existing SNS topic.
Choose Create Alarm.


3. Create a CloudWatch alarm based on a static threshold

In the navigation pane, I chose Alarms, All alarms.
Chose Create alarm.
Chose Select Metric.
Do one of the following:
Choose the service namespace that contains the metric that you want.
In the search box, I entered the name of a metric then press Enter. Then, chose one of the results and continue until a list of metrics appeared. I Selected the check box next to the metric that I want.

Chose the Graphed metrics tab.

Under Statistic , I chose one of the statistics or predefined percentiles, and specified a custom percentile.
Under Period, I chose the evaluation period for the alarm. 

Choose Select metric.

Under Conditions, specify the following:
For Whenever metric is, I specified the metric should be greater than specify threshold value.
Choose Next.
Under Notification, I selected an SNS topic to notify when the alarm is in OK state, or INSUFFICIENT_DATA state.
To have the alarm send multiple notifications for the same alarm state or for different alarm states, I chose Add notification.
When finished, choose Next.
Enter a name and description for the alarm. The name contain only ASCII characters. Then chose Next.
Under Preview and create, confirm that the information and conditions are what you want, then choose Create alarm.



Guide:
https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/gs_monitor_estimated_charges_with_cloudwatch.html

https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html

https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html








