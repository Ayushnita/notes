# __Room Booking System__ # 

## Overview:  ## 

In this project we are trying to create a room booking application microservices Arcitecture. In whih we have to book a rooms for end User.  

## Objective ##

Objective for this project is to test your microservices skills. In this Assigment you create few Microservices using Spring, SpringBoot, Java11 and try to communicate between them using Rest Template.    

you user Eureka for service Discovery, Once this is done then you secure your application using Spring Sercurity for that you create a seprate service for USer Registation and then secure other service.  

After securing you try to achive Event Driven Communication between Notification service and Hotel Booking Service using AWS Kafka.  



---
This Project Consist of below mention Microservices:  
1. HotelBooking Service  
2. RoomSearch Service  
3. Payment Service  
4. Notification Service  
5. User Registation Service   

NOTE:: you also required __Eureka Server__ for service discovery.  

---  

### 1. HotelBooking Service:- ###   
	This Service is exposed to outter word from where we collect all information related to User booking like toDate, fromDate, noOfPersons, Room Type and then we call our _RoomSerach service_ for geting our rooms numbers and send back to End User. Once End User Confirms and call payment API, we call *payment Service* and collect paymet(Dumy) after collecting payment we return a trancationID to HotelBooking Service. This Transaction Id and Booking Id Visible to end user Now and then with the help of Kafka and notification service we send Email and message to End User (Print on Console)    


### 2. RoomSerch Service:_ ###   
	This service is not visible to Enduser, this is for searching roomNumber for given parameters.  
	This Service contain Endpoint that return you room number for you booking.  

### 3. Payment Service:- ###  
	This is dumy payment service, this service call by hotel booking service for payment after confirming rooms by end user. This service return you a paymentID, which is store in both _roomsearch service_ or hotelbooking Service.  

### 4. Notification SErvice:- ###  
	When payment is done and all data is saved properly hotel booking service put a message Object on Kafka topic and then this service read that message from that kafka topic and public message to Console (Try to make a sinario for Email and message Notification). 

### 5. User Registation Service. ###  
	todo:  
