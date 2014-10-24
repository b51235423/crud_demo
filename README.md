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
  2.1.1 Create a SQL Server database named db.mdf
  2.1.2 Using SQL command to create a table for threads
      "CREATE TABLE thread (ID Int, author Varchar(50), email Varchar(50), title Varchar(50), context Varchar(MAX), t        Datetime, view Int, reply Int);"
  2.1.2 Using SQL command to create a table for replies
      "CREATE TABLE reply (ID Int, author Varchar(50), email Varchar(50), context Varchar(MAX), t Datetime, threadID         Int);"
  
  2.2 View
  2.2.1 Index page
      A list of threads from recent to past using SQL command "SELECT ID,author,title FROM thread ORDER BY t DESC"
      A link to change the list to show threads from past to recent using SQL command 
      "SELECT ID,author,title FROM thread ORDER BY t"
      A link to change the list to show threads ordered by view count using SQL command 
      "SELECT ID,author,title FROM thread ORDER BY view DESC"
      A link to change the list to show threads ordered by reply count using SQL command 
      "SELECT ID,author,title FROM thread ORDER BY reply DESC"
      A textbox and a submit button for user to search thread title, author or context using SQL command
      "SELECT ID,author,title FROM thread WHERE title like '%INPUT%' or author like '%INPUT%' or context like '%INPUT%' ORDER BY t DESC"
      
  
  2.3 Control
      /default 
      /default_
  
</pre>
