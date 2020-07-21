# __Spring Notes__  

* Spring is a framework which is build on java. It is a Inversion on control container.  
* Container is mainly used for mainting objects.  
* Spring boot is for mainly making easy to create stand-alone, production-grade spring Application and expose them as a service  
* __Microservices__ break large system into number of independent application that collobrating components.  
* __Spring Cloud__ This is build upon spring boot to make microservices devlopment easier.  

## __Spring Framework__  

* Light weight comprehesive framework for building Java SE and JAvaEE application.  
* _Created by ~~Rod Johnson~~_  
* Uses IOC principal with the help of DI.  
* Provide different framework for devloping application --> MVC, AOP, Security.  
 
## 

* All Dependency are injected by IOC.  
* At runtime  
* Inject in concrete class.  
* Cohesion means all diffrent object combine together to work but they are indeoendent.   
* Swap functionality without changing code.  

## __IOC__  

* No need to create object but describe how they shoud be created.  
* Inversion of responsiblity with regards to Object create and managed.  
* Beanfactory is a represntation of IOC container.  
* BeanFactory is a Interface.  
* BF is the topmost interface in spring interface.  
* Implementation of BeanFactory:-  
	* XmlWebApplicationContext  
	* XmlApplicationContext  
	* AnnotaionApplicationContext  
	* AnnotationWebApplicationContext  
	* classpathApplicationContext  
	* FilePathApplicationContext  
* Sub Interface of BF are Application Context.
	* Difference between BF and AC.  
* BF is used to iniciating, configuring, managing Objects.  
* 


## __Beans__  

* This is a object that is created, instanciated and managed by IOC.  
* Bean are singleton buy default.  

## __configuration MataData__  

This is a java class that contain configuration and also xml in older version.

