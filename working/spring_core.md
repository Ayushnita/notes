# __Spring Core By Udemy__  

## _Q1:_ What is dependency Injection and what are there uses ?  
Answer::  
When you write any code and you are creating any object inside that code you are dependent on that object/class means if the same work you require to do in another way you require to change in code or
the class which is creating that objects. Now how you can handle this situation ? if you pass object in cunstructor of class from outside then it is not dependent on that object and you can easly anyone
can use that class according to its requirement and also in test cases you can pass mock from outside.  
For Example please have a look on GitRepo:


## _Q2_: What is pattern and how it will help in Spring(DI)?    
Answer::  
Pattern is a way to solve a well known problem statement in a specific way which is developed/find by many other developers over the time. This is a well known and eddicient way to solve this problem.
There are numbers of pattern which are also divided in diffrent groups, this is a seprate talk and require a lot of time.DI is also a pattern and well known way to apply. There are alo anti pattern which are just opposite of this.  

## _Q3_: What is interface and how it is very important for DI? 
Answer::  
In point of java it a collection of __abstract function__ and use as a contract for those class which implement them. Interface fouce a class to define all functions which are define in interface.
This is very usefull for testing and interchangebility.   
In pont of Spring it allow JDK dynamic proxy, Implimentation hiding (No class is public only the interface is public and you can you that only), Easy to switch beans (This is DI, In class you make a ref
of a interface and then you pass implimented class(beans) from outside . __DI__)   
For Example please have a look on GitRepo:  

## _Q4_: What is Application Context ?  
Answer::  
__Application Context__ is central part of Spring, this is rewsponsible for may things like   
* initating Beans  
* configure beans  
* Assemble beans  
* Manage bean life cycle  

This means bean related all things are handle by Application context and this is also responsible for _BeanFactory, resource loader, Event registered and listners and property resolver_.  Application ctx
require configuration for beans knowns as metadata which is mainly provideed by xml, annotation and java code, On basis of this it is divided in areas.  
There are diffrent type of Context in Spring:-  

* __AnnotationConfigApplicationContext__ : In this we provide configuration by annotation.  
* __AnnotationConfigWebApplicationCtx__ : In this we provide config by annottion but for web application not standart application.  
* __ClassPathXmlApplicationCtx__ : This is where you provide config by xml file present in classpath only.  
* __FileSystemXmlAWpplicationCtx__ : This is where you provide config by providing config using xml which is present any where in file system.  
* __XmlWebApplicationCtx__ : This is for web application in which config provided by xml.  


## _Q5_: What is container and its life cycle?  
Answer::  
Let take a Example, if have to make a rest API then you have to configure every thing foe http, sest and other thing but if you get a environment where you get all configuration setup by default and 
you only require write bussiness logic that is good one. This is container, you can read more in docker or contaier concept sepratly.  
Life Cycle of Container in Spring::  
* Application Started  
* Spring Container Created  
* Container Read Config  
* Beans created from config  
* Post Process for modify bean run  
* Bean Created ( still no property value set)  
* Bean dependency injected  
* Post processor  
* Run time  
* Application shutdown  
* Ctx Close  
* dstruction method call  

## _Q6_ : How you are going to create a instance of an Applicaiton Context ?  
Answer::  
There are many ways to create a Application context depends for which type of Application Context you want to create like  
* __Non-WebApplication__ :  
	* AnnotationConfigurationApplicationContext :  In this create a instance of __AnnotationConfigurationApplicationContext__ Class by passing a class which is config class containing bean annotated with  __componentscan__ or you can provide bean using __@Bean__ (for third part libs)  and you can also pass base package or use scan method to set base package for config location.  
	* ClassPathXmlConfigContext : In this case we are providing config using xml file which is present in classpath location this xml file contain all beans related configuration.  
	* FileSystemApplicationContext : In this we provide xml as same as before but this time  xml file present anywhere in file system.  
* __WebApplication__ :  
	* Web.xml :  In web application we have to provide a Web.xml file in which we provide servlet, ContextLoaderListner ( which take care of xml ) which load all config for spring beans other thing all are same in beans.xml file.  
	* Java Based : This is a annotation based configuration in which you provide empty web.xml file and all configuration came in a class which implements __WebApplicationInitlizer__ interface and 
create a object of __XmlWebApplicationContext__ and set everything there.  
	* Annotation Based : Everything is same as above case only diffrence is in place of __XmlWebApplicationContext__ you provide __AnnotaionConfigWebApplicationContext__ class Pbject.  Then you provide beans.  
* __SPRINGBOOT__ :  
	* SpringBoot : In this you only provide _@SpringBootApplication_ Anotation and this will scan all other things as usal.  

## _Q7_ : Life Cycle of bean in Application Ctx ?  
Answer::  
There are mainly three phase in any Spring applicatin :-   
* __Context Creation__ :  
* __Bean Created__ :  
	* instance of bean created  
	* properties and dependencies are set  
	* _Bean post processor :: postProcessorBeforeIntilization_  
	* _@PsotConstruct_ called  
	* _initlizingBean:: afterPropertiesSet_  
	* _@Bean(init method)_ called  
	* _BeanPostProcessor:: postProcessorAfterInitlization_  

* __Bean Destroyed__  
	* @PreDestroyed  
	* _DesposableBean:: destroyMethod_ called  
	* _@Bean(destroyMethod)_ called.  

As we can see there are various method called in different places after creation bean setting values and other thing.  
TODO:: Find used of every method why it is added in lifecycle as a hook.  

## _Q8_ : How to create a Application context in Integration test ?  
Answer::  
In this is very easy to create application context for testing sepratelly, there are three steps:-
* Add spring testing dependency in classpath  
* Add _@RunWith(SpringRunner.class)_ on test class  
* Add _@ContextConfiguration(classes = ...)_ in place ... you provide ApplicationConfiguration.class or all other classes for which you want todo testing.  

After doing all avobe three steps all beans are avilabel to you for testing purpose. Here in place of ... you may provice test spacific config.  

## _Q9_ : Prefred way to close a application context, and springboot for this ?  
Answer::  
This depend on which type of application you are working :-   
* Non-Web Application:  
	* Register shutdown hook by calling ConfigurableApplicationContext#registerShutDownHook (Prefered)  
	* call close method directly.  
* Web Application:  
	* Automatically an event set by servlet and send to container that will close this.  
* SpringBoot:  
	* Automatically using shutdownhook for non web and ContextLoaderListner for web.  
