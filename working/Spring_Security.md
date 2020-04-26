# __String Security__

## __Introduction__

* In Spring security we mainly Extend Web Security Adapter class and put two annotation _@configuration and _@EnableWebSecurity
* In This Exended Class There are two type of methods avilable one for authentication and other for authorization, both methoda are overloaded _configuration_
* Diffrence between both overloading functions are in perameter type:
	* AuthenticationManagerBuilder
	* HttpSecurity


This is normal how you start applying Spring security and now we discuss diffrent ways you can use to apply spring Security

## __AuthenticationManagerBuilder__


### __In Memory Spring Security__

### __JPA for Spring Security.__

* to use JPA means  you required to persist data and due to this we are using _Spring User_ 
* Make a class User and then implement _UserDetails_ interface that will provide a basic functions 
* Make this class as a _Entitiy_ so now you can use repositatory
* Entend this repo with __CurdRepository__ and also provide one more function _findByUsername_ 
* Now make service with fucntion _loadUserByUserName_, This function take username as a input and return _Userdetails_ if it did not found ann object then throw _Exception_ __UsernameNotFound__ 
* Now in config function we only provide userrepo using functin __userDetailService__ 
* You also required to give Encoder for password.
----
## __HTTPSECURITY__

### __Things we can do with this config function __

* Secure certain web Url to access basis of role.
* Configuire custom login page
* Logout from application
* Configure cross site request protection

__Example for code __

> 
	http.  
		.autherizeRequests()  
		.antMatchers("/URL", "/URL")  
		.hasrole("ROLE")  
		.antMatchers("/**", "/")  
		.permitAll()   


----

# How Spring work under hood

__In Spring we use __AbstractSecurityInterceptor__ for handling intial authorization of and incoming request. This Interface has two concreate implementation 
	*FilterSecurityInterceptor
	*MethodSecurityInterceptor  -- This require to implement method level Security

To Start methos level security we require to add __@EnableGlobalMethodSecurity(prePostEnabled, securedEnabled)__  

Due to this we have now MethodlevelSecurity Enabled

* __@Secured__ This is a method level annotation and can we used at any funtion. Take String or comma seprated roles but not able to use SPEL Expression.

* __@Pre/POST__ This can be used for SPEL and this can be usefull this can help when Expression required and for role required hasRole function.

* __RoleAllowed__ this annotation enabled by jsr250Enabled

----

# __Creating Custom Filter__

* We require to implement __GenericFilterBean__ this is simple a javax.servlet.Filter
* We require to Overrride __doFilter__  function take request, response and chain as a input.
* This can be added in filter chain by using __addFilterAfter__ , __addFilterBefore__ , __addFilterAt__ and __addFilter__
* Both funtion take two argument your security class and filter class after which you want to put this filter.


--- 


# __Cross Request Forgery __ 


