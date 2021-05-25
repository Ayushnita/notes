Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: aws
Topic: Aws SQS  


---

Awazon Simple Queue Service.  

Step:  

__Question__ how to create a queue in AWS?  

* select sqs in dashboard.  
* There are two type of queue (Standard and FIFO)  
* Standard --> unlimted.  
* FIFO  --> 300  
* create a quick queue or configure queue.  
* Clcik on action.  
* send Message.  
* you can also configure after you create message.  


---   

__Question__  how to handle same using java?  

* create a sqs clinet.  
* get Queue url.  
* use send message using _sendMessage_  


--> Other methods.  

recieveMessage, deleteMessage, etc   

---  

There is one issue in which consumer not listning for all time and for that you require to use JMS.   

Steps:  

* Create a connevtion Factory.  
* create a client (wrapper on SQS)  
* create AWS queue.  
* Create a session from connection.  
* Create a Java Queue from session (createQueue)  
* create a producer.  
* create text message in session.  
* send message.  
* create a consumer  
* setMesageListner which is a class overriding MessageListner  
* startlistner using start.  


