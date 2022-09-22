# Setting Up a SNS architecture


1. To Create a topic

I Signed in to the Amazon SNS console.
In the left navigation pane, I chose Topics. On the Topics page, I chose Create topic.
By default, the console created a FIFO topic. I Chose Standard.
In the Details section, I enter a Name for the topic.
I Scrolled to the end of the form and chose Create topic.
The console opened the new topic's Details page.

2. To Create a subscription to the topic

In the left navigation pane, I chose Subscriptions.
On the Subscriptions page, I chose Create subscription.
On the Create subscription page, I chose the Topic ARN field to see a list of the topics in the AWS account.
I Chose the topic that I created in the previous step.

For Protocol, I chose Email.
For Endpoint, I entered an email address that can receive notifications.

Then, Chose Create subscription.

The console opens the new subscription's Details page.

I Checked the email inbox and chose Confirm subscription in the email from AWS Notifications. The sender ID was "no-reply@sns.amazonaws.com".
Amazon SNS opened web browser and displays a subscription confirmation with subscription ID.

3. To Publish a message to the topic

In the left navigation panel, I chose Topics.
On the Topics page, I chose the topic that I created earlier, and then chose Publish message.
The console opened the Publish message to topic page.
In the Message details section, enter a Subject, such as:

Hello from Jesmykel!

In the Message body section, I chose Identical payload for all delivery protocols, and then enter a message body:

Publishing a message to an SNS topic.

Choose Publish message.
The message is published to the topic, and the console opens the topic's Details page.
I Checked my email inbox and verify that I received an email from Amazon SNS with the published message.

4. To Delete the subscription and topic

On the navigation panel, I chose Subscriptions.
On the Subscriptions page, I chose a confirmed subscription and then chose Delete.
In the Delete subscription dialog box, I chose Delete.
The subscription was deleted.
On the navigation panel, I chose Topics.
On the Topics page, I chose a topic and then chose Delete.
On the Delete topic dialog box, I entered delete me and then choose Delete.
The topic is deleted.


Guide:
https://docs.aws.amazon.com/sns/latest/dg/sns-getting-started.html

https://docs.aws.amazon.com/sns/latest/dg/sns-create-topic.html