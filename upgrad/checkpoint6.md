# __Checkpoint 6__ #   

This checkpoint mainly focus on Spring Security and we are going to handle Speing security Using JWT.



## TODO : 1 ##   

* Create a new Microservice _UserRegistationService_ using Spring Initlizer.   
	* __Project__ : Maven Project    
	* __LAnguage__ : Java   
	* __SpringBoot__  : 2.4.4    
	* __Project MetaData__  : 
	* __Group__ : com.sweethome   
	* __Artifact__ : userregistationservice
	* __Name__ : userregistationservice
	* __Description__ : This service is aminly desgin for handling User Validation.   
	* __Packaging__ : Jar   
	* __Java__ : 11   
	* __Dependencies__  :  
		* Spring security   
		* Web   
		
Generate Project and Extract that in SweetHome Folder.   

Note : Add two more dependencies for handling JWT in pom xml file.      

<dependency>  
    <groupId>io.jsonwebtoken</groupId>  
    <artifactId>jjwt</artifactId>   
    <version>0.9.1</version>   
</dependency>   
<dependency>   
   <groupId>javax.xml.bind</groupId>   
   <artifactId>jaxb-api</artifactId>   
   <version>2.3.1</version>   
</dependency>   

---   

## TODO : 2 ##     
* Open UserRegistationService in your IDE.   
* Create below mention packages  
	* config  
	* controller  
	* helper   
	* model   
	* service   


## TODO : 3 ##   
* Create class SecurityConfig in _config_ package.   
* Annotate this class for security Enabling.  
* Annotate this class for Configuration.  
* Create Bean For passwordEncoder, returns __NoOpPasswordEncoder__   
* Create Bean for AuthenticaitonManager.   
* Override configure(AuthenticationManagerBuilder) and configure(HttpSecurity)   
* In Configure(HttpSecurity) methods, disable cors, disable csrf, permitAllRequest, sessionManagment will be stateless.   

## TODO : 4 ##     
* Create JwtUtil class in helper package.   
* Copy this class from https://raw.githubusercontent.com/koushikkothagal/spring-security-jwt/master/src/main/java/io/javabrains/springsecurityjwt/util/JwtUtil.java   

## TODO : 5 ##   
* Create two model class in model package.  

1. JwtRequest  -->
	This class handle GenerateToken Request.  
	private String userName;
	private String password;  


2. JwtResponse  -->   
	This class handle Jwt Response   
	private String token;    


Cerate Getter / Setter / NoArgs Cons / AllArgs Cons   


## TODO : 5 ##   
* Create class CustomUserDetailService in service package.    
* Create one feild userMap of type Map<String, User>   
* In Constructor Provide   
	this.userList = new HashMap<>();  
	userList.put("upgrad", new User("upgrad", "upgrad123", new HashSet<>()));   
	userList.put("student", new User("student", "student123", new HashSet<>()));  
	userList.put("user", new User("user", "user123", new HashSet<>()));   
    	userList.put("admin", new User("admin", "admin123", new HashSet<>()));   

* implement UserDetailsService intefrace by Spring Security   
* Override loadUseByUserName   
* This method take username as a input and check if userName exist in map, if yes return User else throw UsernameNotFoundException.    
* Annotate this for registring in Spring Context.   


## TODO : 6 ##   
* Open SecurityConfig class  
* Override configure(AuthenticationManagerBuilder)   
* Provide CustomUserDetailService for Authentication.  


## TODO : 7 ##   
* Create RegistationController in controller package.   
* make it a rest controller   
* Autowire __JwtUtil, AuthenticationManager, CustomUserDetailService__    
* Create two endpoint  

	URL -> /token  
        HTTP METHOD  --> POST  
        Return Status --> Created  
        RequestBody  --> JwtRequest                                                 
        Return type --> JwtResponse     

	This end point take userName and password as a input and return a JWT token.  
	first laod userDetails for userDetailService and then generate token using detail.   



	URL -> /validate    
        HTTP METHOD  --> POST  
        Return Status --> Created  
        RequestBody  --> JwtResponse   
        Return type --> User  

	This end point take jwt token as a Input and then find username from that token after that find UserDetail and return back.  


## TODO : 8 ##  

* Create a MyUser Class for handling /validate endpoint output in model package.    
* Class implement UserDetails  
* Provide below mention feild   
	private String password;  
	private  String username;  
	private  Set<GrantedAuthority> authorities;  
	private  boolean accountNonExpired;  
	private  boolean accountNonLocked;   
	private  boolean credentialsNonExpired;   
	private  boolean enabled;   

* provide getter and setter for all feild .  
* make sure override method return propoer value.  


## TODO : 9 ##   

* Open BookingService   
* Add Spring Security Dependency  
* Create class JwtFilter class in config folder   
* Extend class with OncePerRequestFilter   
* Override doFilterInternal method.  
	* In this method find jwt token form header (Authentication)   
	* Check header is not null and start with "Bearer " space is ther.  
	* Remove "Bearer " from header for token.   
	* user RestTemplate (do not autowire use new) for hitting /validate endpoint with token.   
	* if user is not null set user in SecurityContextHolder.  

	* donot Call filterChain.dofilter method.  



##  TODO : 10 ##   

* Create class SecurityConfig in config Folder   
* Enable Web Security  
* Make this class as a configuraiton class.  
* extend it with WebSecurityConfigurationAdapter.   
* Override  configure(httpSecurity)  
	This method disable cors, csrf.
	All request required to be autherized   
	Stateless session.  
	Add a filter before all  -> jwtFilter(One which we create) and second perameter as UsernamePasswordAuthenticationFilter.class   
