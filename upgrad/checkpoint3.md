# __Checkpoint 3__ #  

Import Booking Service in your IDE  

---

## TODO: 0 ##

Create Model layer  

* Create a model package.  
* Create below mention model and entity classes.  

1. BookingInformation --> This is a Entity class which map to *hotel_booking* table.  

	@Id  
	@GeneratedValue(strategy = GenerationType.AUTO)  
	private int id;  
	private String userId;  
	private int HotelId;  
	//TODO: Map data class to sql Date.   
	private Date fromDate;  
	//TODO: Map data class to sql Date.   
	private Date to;  
	private String roomNumbers;  
	private String trancationId;  
	//TODO: Map data class to sql Date.   
	// TODO: Only for created Date.  
	private Date bookedOn;   


2. BookingMode (Enum)  --> This represent which type of payment you do in payment End Point and this came as a Request Body feild, so take care of propoer spring handling it.  

	UPI("upi"), NET_BANKING("net_banking"), CREDIT_CARD("credit_card"), DEBIT_CARD("debit_card")   

HINT:  Use @JsonValue and @JsonCreator  on appropiate method.  
  
3. BookingRequest  --> This Model class is responsible for handling request which came in /booking EndPoint.  

	
	private String userId;  
	private int hotelId;  
	private Date fromDate;  
	private Date toDate;  
	

4. PaymentRequest --> This class is paylaod for payment service and send to it using POST HTTP request and retrurn with transaction ID.  

	private int bookingId;  
	private PaymentDetails paymentDetails;  


5. PaymentDetails  --> This model class resposible for handling rest endpoint call for  /booking/payment/{bookingId}  and came as a request body for that end point.  

	private BookingMode bookingMode;  
	private Date bookingDate;  
	private float amount;  
	private String upiId;  
	private String cardNumber;  
---   

## TODO : ##  

Create DAO layer  

* Create package dao   
* Create class BookiningDao for BookingInformation Entity.  
* Annotaate it with proper annotation.  


##  TODO :  ##  

Create Seravice layer  

* Create package __searvice__  
* Create class _BookingService_ and annotate it with annotation  
* Create two methods in class 
	* bookingDetails(BookingRequest br)  
	* doPayment(bookingId, PayentDetails)   

BookingDetails is responsible for /booking Endpoint  
doPayment is REsponsible for /booking/payment/{paymentId} Endpoint.  

Note:  Autowire Dao layer in service Layer and annotate Propoerly for SpringContainer.  

---
## TODO: 1 ##  

Create Controller Layer  

* Create a controller package.  
* Create a BookingController class, which is a resposible for intrecting with outer word using REST API.  


## TODO 2 ##  
This class contain below mention endpoints:  
	 
	 URL -> /booking  
	 HTTP METHOD --> Post  
	 Return Status --> CREATED  
	 Request Body --> BookingRequest (See Model section for this class)   
	 Return Type --> Booking Information  

This Endpoint call Search Service Internally and return back with Room numnbers in hotel if avilable and then Save BookingInformation Entity Class with Updated Room Numbers.  

For now HardCode roomNumbers as "1, 2, 3" in place or calling search Service.
Create a BookingInformaiton class Object with help of Data avilable in Booking Reques and Room numbers which you hard Code and save in database.



	URL -> /booking/payment/{bookinId}   
	HTTP METHOD  --> POST  
	Return Status --> Created  
	RequestBody  --> PaymentDetails  
	Return type --> BookingInformation  
	

This Endpoint take bookingId in url path and PaymentDetails in Body and then search for given bookingId and check for trancationId, if it is null then call payment service for trancation Id and save in booking service.  

For now hardcod trancation Id and update bookingInformation class and return back.   


NOTE:: 
* Service required to be divided in 4 layer structure [ Model , Dao, Service, Controller ]  
* All class level feils required to be constructor Autowired not feild or setter autowired.  
* All bussiness Logic goes in Service layer.  

---  
