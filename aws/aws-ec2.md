Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: aws
Topic: EC2 AWS 


---

NOTE:  Dedicated dashboard for EC2.  


Steps:: 

* click on __launch instance__  
* choose a Amazon machine Image __AMI__  
* select type (means configuration / cpu and ram)   
* click next   
* see all configuration and modify them.   
* VPC is virtual private network.  
* seclect size of volume or create a new volume.   
* configure security group.  ( provide all port details like ssh, tomcat etc)  
* custom TCP rule.  
* clcik on __review and launch__  
* Download keypair.   
* click on __launch__  


---   

they provide public IP where you can connect to this host.  
Learn how to convert bm file into pk file using putty gen.  
By default user is ec2-user.  
while using loging you can use autrization for providing private key.   
EC2 hour calculation for free tier is 750 hrs and if you start any instance also it calculate it as one hour.  

----   

## __Deploying applicaiton in EC2__   

you require to transfer jar file from host to ec2 instance using WINSCP (Question how to do that in linux or mac)  
Copy in home folder.   
once jar is copied, run application useing __java -jar__  command.  
once it start runnign you require to go in __security group__ and expose end point.  
There are two type of ports __inbound__ and __outbound__ .   
Inbound is for how can hot your service.  
Outbound is for to whom our service can communicate.  


---   

## __How to access s3 using ec2 instance__  

create one __IAM__ user (role) attach to ec3 for full s3 access.   

* Click create roles  
* select service which are going to use it. 
* provide access to role.  
* provide tag.  
* provide role name.   
* click on create role.  
* go to ec2 instance.  
* click on action 
* instance setting  
* attach role.  


----   

NOTE:: to communicate between services we required to use roles.    

This is not a Ideal way you can use code commit, code deploy and other things.  
