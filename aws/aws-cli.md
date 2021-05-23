Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: aws
Topic: aws cli 


---

__Queation__ AWS cli seting and configuration?  

* Browse download aws cli   
* download cli  
* aws configure 
* provide default region name  
* default output format  

--> good to connect  

There are few global buckets and you can see them using: 

aws s3 ls  

NOTE: aws create few files that contain all config for you.    

--> create a new bucket.   
aws s3 mb s3://<name of bucket>  --> global bucket.  

--> upload a file in s3
aws s3 cp <file name> <bucket name>   

--> list all file in a particular bucket. 
aws s3 <bucket name > ls 


#  __Commands__   

aws --version
aws configure --> use to configure aws use passward and use in you system
aws s3 ls --> all buckets avilable for user
aws s3 mb s3://<name of bucket>  --> to create a new bucket.  
aws s3 cp <file name> <name of bucket>  --> to upload things in bucket.   
aws s3 <bucket name> ls  
