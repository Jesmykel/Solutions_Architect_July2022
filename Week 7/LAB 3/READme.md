# Working with SQS


1. To Create a queue

I Opened the Amazon SQS console at https://console.aws.amazon.com/sqs/.
Chose Create queue.
On the Create queue page, I specified the correct region.
The Standard queue type is selected by default. I Chose FIFO.
Entered a Name for queue. The name of a FIFO queue end with the .fifo suffix.

To create your queue with the default parameters, I scrolled to the bottom and choose Create Queue. 


2. To Send a message

From the left navigation panel, I chose Queues. From the queue list, I selected the queue that I created.
From Actions, I chose Send and receive messages.
The console displayed the Send and receive messages page.
I Entered text in the Message body
I Entered a Message group id for the queue. 
I enable content-based deduplication. 
Then, Chose Send message.


3. To Receive and delete your message


From the Queues page, I selected a queue.
From Queue Actions, I selected Send and receive messages.
The console displayed the Send and receive messages page.
I Chose Poll for messages.
To delete message, I selected the message that I want to delete and then chose Delete.
In the Delete Messages dialog box, I chose Delete.


4. To Delete your queue

From the queue list, I selected the queue that I have created.
From the Queues page, I selected the queue to delete.
Chose Delete queue.
The console displayed the Delete queue dialog box.
In the Delete queue dialog box, I confirmed the deletion by entering delete.
Then, Chose Delete.



Guide
https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-getting-started.html

https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-configuring.html