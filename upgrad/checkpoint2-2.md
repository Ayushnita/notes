# __Search Service__ #  

This Service is responsible for finding Room according to given _Query Params_ provided and once room Got Confirmed you have to save those rooms detais in your database.   


## TODO : 1 ##  


* Import Seach Service in your Project.  
* Create four Different Packages.  
	* model  
	* dao  
	* service  
	* controller   
* Provide spring properties to run this service on 8081 and connecting with database.  


## TODO : 2 ##   
Create below mention model or Entity classes in model package.   

1. RoomBookingDetils:  
	This is a Entity class for storing booked rooms details in database.  

	@Id  
	private int bookingId;  
	private int roomId;  
	private Date fromDate;   
	private Date toDate;  
	private String userName;   
	private String adharNumber;   
	private int paymentId;   

Table from whcih you required to connect is **booking-details** and please provide propoer annotation for date and automatic Id (Primary Key) generation.    

  

2. RoomDetails:  
	This Entity class mainly use to save all romms details which are avilable in database and provide general information about rooms.  


	@Id  
	private int id;  
	private RoomType roomType;  
	private int capacity;  
	private float rate;  
	private boolean isOpen;  


This Entity class connect with **room-details** table in database.  
Please provide proper annotation for making it Entity clas and connect with table, also for auto-generating database primary key.   


3. RoomFindRequest:   

	This Model class used to convert queryParam which came in httpRequest into a class.   

	private Date fromDate;  
	private Date toDate;   
	private int roomCount;   
	private RoomType roomType;  


4. RoomType  :  

	This is a Enum which came as a request param in endpoint and you have to proive propoer annotation for spring to handle it.   

	DELEX, NORAL


5. SaveRequest:  

	This Class is responsible for handling save request for Rooms Booking.   






## TODO : 3 ##  

Create a dao interface  name _SearchDao_ and _RoomInnfoDao_


1. SearchDao:  

	This interface is responsible for handling RoomBookingDetails.   
	Extend JPARepository<RoomBookingDetails, Integer>   
	write one menthod findBookedRooms  -> This method is resonsible for finding all booked Rooms between two given Dates. (toDate, fromDate)   

	Use @Query annotaion and provide a sql query there if required.   


2. RoomInfoDao:  

	This Interface is responsible for roomdetails   
	Extend JPARepository<RoomDetials, Integer>   
	write a method findByFoomType  --> this is responsible for finding all rooms of specific type and return a list of roomnumber.   




## TODO : 3  ##    

* Create a class name SearchService annotate with propoer annotation for creating Spring Bean.   
* AutoWire SearchDao and roomInfoDao using constructor autowiring.   
* Create two methods:  
	* findRoomIds   
	* saveBookingDetails   


1. FindRoomIds:  
	This method is responsible for finding all rooms Ids which are empty and avilable for booking and return a list of them.  

	first find all rooms by type which are avilable in hotel.  
	Second find Booked rooms from given dates.  
	remove booked rooms from all rooms list.  
	return list.  

2. SaveBookingDetails:  
	This methhod is responsible for saving booked rooms details in database.    


## TODO : 4 ##  

* Create a class SearchController.   
* Annotate it to make it a RestController.  
* Autowire Service layer.  
* Create two EndPoint  

	* __URL__ : /search  
	* __HTTP METHOD__ : get   
	* __RequestBody__  :   
	* __queryParams__ : fromDate, toDate, roomCount, roomType
	* __Response Status__ : Ok
	* __Response__ : List<Integer>   

	
	
* Create two EndPoint  

	* __URL__ : /search/save  
	* __HTTP METHOD__ : GET   
	* __RequestBody__  :  SaveRequest   
	* __Response Status__ : Created  
	* __Response__ : int (id)   

