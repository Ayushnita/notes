# __Checkpoint 4__ #  

## TODO: 1 ##  

Enable Eureka client for Booking service, Payment Service, Search Service.  

For this you require to annotate main class with proper annotation and provide proper propoertie in applicaiton.propoerties file.  

Your Eureka client shoud fetch services details from Eureka server and Register itself with Eureks server.  

## TODO: 2 ##  

Open Booking Service and create a config package.  
Create a class AppConfig.java in config package.  
Annotate class with poper annotation so that it start registing Beans in Spring Context.  
Catea a Bean for loadBalanced RestTemplate. 

## TODO: 2.5 ##  

In BookingService class autowired RestTemplate.  
Constructor Autowiring only.  


## TODO: 3 ##  

Now in Place of hard Coded Room numbers call room service with help of Rest Template and use return type.  
Call Endpoint Whcih return roomNumbers and join them with **,** .  


## TODO 4 ##  


In Place of hardCoded Transaction Id call Payment Service with the help of Rest Template.  
And now use transaction Id return by api and save it in bookingInformation and return back,  
