<pre>
crud_demo
using a discuss system as an example

TODO list
=========

1.functions
  1.1 Create
  1.1.1 Visitors can open a new thread. Input fields including name, email(optional), title, context. 
  1.2.1 Visitors can reply to a exist thread. Input fields including name, email(optional), reply.
  
  1.2 Read
  1.2.1 A index page with list of existing threads' title and their authors with a link to show full thread.
  1.2.2 A page to show title and context of a thread and replies.
  
  1.3 Update
  1.3.1 Administrator can edit thread title or context.
  
  1.4 Delete
  1.4.1 Administrator can delete a thread or a reply.
  
  1.5 Search
  1.5.1 Visitors can search threads according to its title, author or context.
  
  1.6 Sort
  1.6.1 Visitors can sort threads according to its date, view count or reply count.

2.implementation steps
  2.1 Model
  2.1.1 create a SQL Server database named db.mdf
  2.1.2 using SQL command to create a table for threads
    CREATE TABLE threads
    (First_Name char(50), Last_Name char(50), Address char(50), City char(50), Country char(25), Birth_Date datetime);
  
  
  2.2 View
  
  2.3 Control
  
</pre>
