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
  
  1.7 Extra functions
  1.7.1 A more efficient search can be implemented using cosine similarity compare.

2.implementation steps
  2.1 Model
  2.1.1 Create a SQL Server database named db.mdf
  2.1.2 Using SQL command to create a table for threads
      "CREATE TABLE thread (ID Int AUTO_INCREMENT, author Varchar(50), email Varchar(50), title Varchar(50), context        Varchar(MAX), t Datetime DEFAULT GETDATE(), view Int, reply Int);"
  2.1.2 Using SQL command to create a table for replies
      "CREATE TABLE reply (ID Int AUTO_INCREMENT, author Varchar(50), email Varchar(50), context Varchar(MAX), t            Datetime DEFAULT GETDATE(), threadID Int);"
  
  2.2 View
  2.2.1 Index page
      A list of threads from recent to past using SQL command "SELECT ID,author,title,t FROM thread ORDER BY t DESC"
      A link to change the list to show threads from past to recent using SQL command 
      "SELECT ID,author,title,t FROM thread ORDER BY t"
      A link to change the list to show threads ordered by view count using SQL command 
      "SELECT ID,author,title,t FROM thread ORDER BY view DESC"
      A link to change the list to show threads ordered by reply count using SQL command 
      "SELECT ID,author,title,t FROM thread ORDER BY reply DESC"
      A textbox and a submit button for user to search thread title, author or context using SQL command
      "SELECT ID,author,title,t FROM thread WHERE title like '%@KEY%' or author like '%@KEY%' or context like               '%@KEY%' ORDER BY t DESC" and INPUT should be detect for SQL preserve words and remove.
      A form for visitor to post a new thread including textboxes for title, context, name, email and a submit button
      using SQL command to add new thread.
  
  2.2.2 Thread page
      Using SQL command "SELECT ID,author,email,title,context,t FROM thread WHERE ID = @ID" to get author, email,           title,context of a thread and show in a table tag.
      Using SQL command "SELECT ID,author,email,context,threadID,t FROM reply WHERE threadID = @ID ORDER BY t DESC" to       show replies of current viewing thread.
      Two Textboxes for reply name and reply context, and a submit button. Using SQL command to create new reply to a       thread
      
  2.2.3 Administrator page
      After pass a identification process for administrator, a visitor can access a page with following options 
      A. update a thread's title or context (Thread ID,title,context required)
      B. delete a thread (Thread ID required)
      C. delete a reply (Reply ID required)
    
  2.3 Control
  
      HomeController
      
      /index
      /index?sort=S
      /index?search=KEY
      show page described in 2.2.1
      
      /thread?id=ID
      show page decribed in 2.2.2
      
      /submit_thread?n=NAME&e=EMAIL&t=TITLE&c=CONTEXT
      execute SQL command
      "INSERT INTO thread (author,email,title,context) VALUES ('@NAME','@EMAIL','@TITLE','@CONTEXT')"
      
      /submit_reply?n=NAME&e=EMAIL&c=CONTEXT
      execute SQL command
      "INSERT INTO reply (author,email,context) VALUES ('@NAME','@EMAIL','@CONTEXT')"
      
      /admin
      show options of a administrator as described in 2.2.3
      
      /update_thread?id=ThreadID&t=TITLE&c=CONTEXT
      execute SQL command
      "UPDATE thread SET title='@TITLE', context='@CONTEXT' WHERE ID = @ThteadID"
      
      /delete_thread?id=ThreadID
      execute SQL command
      "DELETE FROM thread WHERE ID = @ThreadID"
      
      /delete_reply?id=ReplyID
      execute SQL command
      "DELETE FROM thread WHERE ID = @ReplyID"
      
  
</pre>
