Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: aws
Topic: Aws Simple Notification Service. (SNS)   


---
 
This is like kafka.  


There is a subscriber and publisher concept.   

STEPS:: 

* provide name  
* Discription  
* click on create topic.  
* add subscription. 
* do required steps for activating subscription  
* publish message.  

---   

__Question__ Now how to achive same thing using JAVA:  

* create snsClient AmazonSNSClientBuilder()  
* publish on topic.  


__Question__  Create one SNS topic?  
* new CreateTopicRequest.  
* snsClient.createTopic(request)  

__Question__ Print the topic ARN?  
* createTopicRquest.getArn();


__Question__ Handle Subscrition?   
* new SubscritionRequest(topic, type, data)  
* snsClient.subscribe(request)  



---  

ARN  -> Amazon Resource Name  

--- 

With the help of subscription you can send email.  

