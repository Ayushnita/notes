# __Notification Service__ #  

Notificatoin service is one of basic and simple service in which user have to require consume message from Kakfa on a particutal topic ___message___ .  

In this service kafka listner consume message and Print two differnt Logs on Console.  
This look loke a service that is sending Email and message Notification to end user after Sucessful Booking.  

---  

###  __LOGS On Console__  ###  

1. First Log Print :-   
	Message:  Hi Your Booking is Conformed. your Booking Id id {Booking}.  See you Soon.   

2. Secon Log Message: :-   
	Email: Hi Your Booking is Confirmed for {toDate} and Booking ID is {Booking Id}. For and help please Contact below Link.   


### __Model Kafka Consume__ ###  

Notification Service Consume a _Json_ Object which Contain below mention feild.  
1. UserId  
2. toDate  
3. bookingId  

NOTE: Above mention all feilds stay inside a class name __Message__  
