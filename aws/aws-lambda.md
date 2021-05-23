Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: aws
Topic: aws lambdas.    


---


# __Lambdas__   

This is mainly about serverless architucture.  

---  

Steps:  

* Create a IAM role for __Lambda__  
* write code.   
	* class require to implement RequestHandler interface
	* This inteface take two input event like s3event and output <string>.  
	* Overrride handleRequest method.  
	* from this event get bucket name (According to event).  
	* now process and code accordingly.  

* add dependecies for AWS lambda.  
* create a jar.  
* uplaod jar in lambda.  
	* Create a appropiate IAM role. <here s3 access role>  
	* Go to lambda section.  
	* click on __create function__  
	* from scrach.  
	* give name.  
	* select language.  
	* provide permission.  
	* click on __create__  
	* Add trigger.  
		* select S3.  
		* select bucket.  
		* enable this trigger.  
	* upload jar file.  
	* provide class name 


---  


