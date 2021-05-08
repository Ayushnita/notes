# __Payment Service__ #  

### Overview ###  

This payment Service is mainly use to handle payments and also maintain a records for all payment done.  

This Service call by Hotel Booking Servic Once All rooms are confirmed by User. There is a no direct call to this service this is done with the help of Eureka Discovery Client.  


### Model Classes ###  

1. PaymentRequest:  
	private int bookingId;  
	private PaymentDetails paymentDetails;  

2. PaymentDetails:  
	private BookingMode bookingMode;  
	private Date bookingDate;  
	private int  bookingId;  
	private float amount;  
	private String upiId;  
	private String cardNumber;  
	

3. BookingMode (Enum):  
	PI("upi")   
	NET_BANKING("net_banking"),   
	CREDIT_CARD("credit_card"),   
	DEBIT_CARD("debit_card")    

4. PaymentDetailsDao:  
	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	private int id;
	private BookingMode bookingMode;
	// match util date to sql date
	private Date bookingDate;
	private int  bookingId;
	private float amount;
	private String upiId;
	private String cardNumber;
	


### End Points ###  

1. /payment:-  

	HTTP METHOD : post  
	This Endpoint take a PaymentRequest as a input and return paymentId(int).  
	This Endpoint crete a PaymentDetailsDao and then save that in database.
	After Saving it return a unique id (payment Id), return back to user.  

2. /payment/{paymentId):-  
	HTTP METHOD : Get  
	This end point mainly take a payment Id form URL and return back paymentDetailDao object to end USer.  





### Propoerties ###  

server.port: 8082 
spring.applicatoin.name= payment-service
