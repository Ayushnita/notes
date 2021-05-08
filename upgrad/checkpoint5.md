# __Checkpoint 5__ #   


PRE-REQUIREMENT:  

Run Kafka on AWS instance.   
Create a topic name __message__.  

## TODO : 1 ##   

* Open Booking Service  
* In model package create a class Message.java contains below mentions feild.  
	private String userId;  
	private Date toDate;  
	private int bookingId;  

NOTE:  This is class which put on Kakfa topic as a json so Create Configuration Accordingly.  

## TODO : 2 ##  

* In Config package create a class name _KafkaConfig.java_ .   
* Annotate with propoer annotation for making it a Configuration class.  
* Create Beans required for Kafka.  



## TODO : 3 ##  

* Autowire Kafka template in BookingSErvice class.  
* In doPaymentMethod, after saving bookingInformaiton in table with Help of JPA send message object to Kafka on message topic.   


## TODO : 4 ##   

* Open notification Service.  
* Create package config, listner, model.  
* Cerate Class KafkaConfig in package config.  
* Annotate class with propoer annotation for Enabling Kafka.  
* Create Beans for ConsumerFactory and KafkaListner.  


## TODO : 5 ##  

* Create message Model class in model package same as mention above.  


## TODO : 6 ##  

* In lsitner package create class MessageListner and make a method name messageListner which will be responsible for listing messgage from Kafa.   
* Add These two lines in method.  


System.out.println("Message:  Hi Your Booking is Conformed. your Booking Id id "+ message.getBookingId()+".  See you Soon.");    
System.out.println("Email: Hi Your Booking is Confirmed for "+message.getToDate()+" and Booking ID is "+message.getBookingId()+". For and help please Contact below Link.");    


