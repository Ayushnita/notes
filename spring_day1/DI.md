Type of DI  

* setter
* constructor  
* field  
* Method  (When singleton and prototye injection cross )  

__NOTES::__ Constructor dependency for mandatory and setter for optional dependency.

To make a pojo class as bean autonation it with @Component  
IOC scan that package and make bean of all classes annotated with @Component and similar annotaion.   
Default name for bean is same as class name in camle case.  
For scaning I create a config class and mark it with @ComponentScan and provide base package and all sub packages will scan. 
To make a configuration annotate with @Configuration annotaion.  
Diffrent way to register bean if it is not created by component scan.  
	* make a method in which you return the object and annotate with @Bean
	* Class must be config class  
	* default name for bean is method name.  


## __Spring Boot__  

* make a java class that is annotated with @SpringBootApplication
* SpringBootApplication --> @Configuration + @ComponentScan + @EnableAutoConfiguration  
* SpringApplication.run(Application.class, args)  
* here args are comamnd line argument  
* return type of run method is configurableApplicationContext.


## NOTES:

get bean is a overloaded method with 
	* class Name
	* bean Name 
	* bean + class Name  


When you have two bean of same type then you have to mark one as @Primary to use first way to create.  
To Change scope from singleton to prototype use __@Scope()__  
When to go prototype thats depend on statefull bean or stateless bean.  
To pass one bean into another we use method name.  

##__ Intilize Bean__  

by deafult all bean are eagerly initlize.  
To make it lazy initlize mark that bean as __@Lazy__  
