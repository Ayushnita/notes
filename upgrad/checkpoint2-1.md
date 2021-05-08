# __Checkpoint2__ #  


## Payment Service ##  

---  

## TODO 1 ##  

* Open Payment Service in your IDE.  
* Create Four Different Package 
	* model
	* dao  
	* service  
	* controller  


## TODO 2 ##   

Create below mention Model and Entity Classes in *model* package.  

1. BookingMode (Enum)  --> This is same class which we ceate in BookingService   
	
	UPI("upi"), NET_BANKING("net_banking"), CREDIT_CARD("credit_card"), DEBIT_CARD("debit_card");      

2. PaymentDetails  --> This class is responsible for all details related to payment and it is not a Entity Class. This class use in PaymentRequst to handle it properly.   
	
	private BookingMode bookingMode;  
	private Date bookingDate;  
	private int  bookingId;  
	private float amount;  
	private String upiId;  
	private String cardNumber;  


3. PaymentDeatilsDao  -> This is a Entity Class and responsible for Saving Data in DataBase.  

	@Id  
	@GeneratedValue(strategy = GenerationType.AUTO)  
	private int id;  
	private BookingMode bookingMode;  
	// Mark Annotaion for converting uitil Date to SQL Date.  
	private Date bookingDate;  
	private int  bookingId;  
	private float amount;  
	private String upiId;  
	private String cardNumber;  


4. PaymentRequst --> This class came as  Request Body for /payment endpoint.  

	private int bookingId;  
	private PaymentDetails paymentDetails;  
	


---   

##  TODO : 3 ##

* Create a PaymentDao class in dao layer and this class responsible for saving data in Database using SpringJPA.   
	Entity Class -- > PaymentDetailsDao   


## TODO : 4 ##   

* Craete a __PaymentService__ class in service package. Annotate it for proper Spring Initlization.  
* Autowire Dao class (Constructor Autowiring)  
* Create method makePaymentService(bookinId, paymentDetails) --> This method call by /payment endppoint.   
* Create method getPaymentById(paymentId)  --> This method call by /payment/{paymentId} endpoint.   


NOTE:: All Bussiness logic went in service layer.   

## TODO : 4 ##   

* Create a __PaymentController__ class in controller package and meke it a __Rest Controller__.   
* Autowire Service layer (Constructor Autowiring)  
* Create endpoint:  
	* __URL__ : /payment  
	* __HTTP METHOD__ : Post  
	* __RequestBody__  : PaymentRequest  
	* __Response Status__ : Created  
	* __Response__ : transactionId (int)   

* Create EndPoint:  
	* __URL__ : /payment/{paymentId}  
	* __HTTP METHOD__ : GET  
	* __RequestBody__  : (PathVaraiable) int  
	* __Response Status__ : OK  
	* __Response__ : PaymentDetailsDao   


