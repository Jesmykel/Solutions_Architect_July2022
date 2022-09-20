# Working with AWS DynamoDB

Task:
1. To Create a Table

I Signed in to the AWS Management Console and open the DynamoDB console at https://console.aws.amazon.com/dynamodb/.
In the navigation pane on the left side of the console, I chose Dashboard.
On the right side of the console, I chose Create Table.
I Entered the table details as follows:
For the table name, I entered Software.
For the partition key, I entered Usage .
Entered Folder as the sort key.
I Left Default settings selected.
Then Chose Create to create the table.


2. To Write Data to a Table Using the Console or AWS CLI

In the navigation pane on the left side of the console, choose Tables.
In the table list, I chose the Software table.
I Selected View Items.        
In the Items view, I chose Create item.
I Chose Add new attribute, and then choose Number. Named Size .
I Repeated this process to create a Placement of type String.

Entered the following values for your item:

For Software, I entered kali linux.
For Usage, I entered Cybersecurity.
For Size, I entered 10 .
For Placement, I entered Admin.

Choose Create item.
                              
I Repeated this process and create another item with the following values:

For Software, I entered Excel.
For Usage, I entered Data Entry.
For Size, I entered 5 .
For Placement, I entered Secretary.

I Did this one more time 

For Software, I entered Darkweb.
For Usage, I entered Browsing.
For Size, I entered 1 .
For Placement, I entered Technicial.

3. Read Data from a Table

In the navigation pane on the left side of the console, choose Tables.
Choose the Software table from the table list.
Select the View items.
On the Items tab, view the list of items stored in the table, sorted by Usage.

4. Update Data in a Table

In the navigation pane on the left side of the console, chose Tables.
I Chose the Music table from the table list.
I Chose View items.
I Chose the item whose Usage value is Kali linux and Folder value is Security.
I Updated the Usage value to Updated Usage, and then choose Save.

5. Query Data in a Table

In the navigation pane on the left side of the console, choose Tables.
I Chose the Software table from the table list.
Choose View items.
Choose Query.
For Partition key, enter Kali linux, and then choose Run.

6. Create a Global Secondary Index

In the navigation pane on the left side of the console, choose Tables.
I Chose the Software table from the table list.
Choose the Indexes tab for the Software table.
Choose Create index

7. Query the Global Secondary Index

In the navigation pane on the left side of the console, I chose Tables.
Chose the Software table from the table list.
I Selected the View items.
Chose Query.
In the drop-down list under Query, I chose SOftware-index.
For Softawre, entered Kali linux, and then choose Run.

8. Clean Up actions

I deleted the index, item then the table created.


Guide:
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStartedDynamoDB.html