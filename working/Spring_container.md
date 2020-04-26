# __Spring Container__

Inversion of control is same as DI. This is responsible for creation of Object. It is the process where objects define their dependencies with other object.  
he way why which beans created are  
* constructer method   
* factory method  
* propeties once bean created and return from factory  
Then container inject dependency bhen it create a bean.


This can be happen by using __Service locator pattern__ or by __Direct custruction of classes__ .  Main pachages responsible for this are _org.springframework.beans_ and _org.springframework.context_.   
There are two intrerface for this  
* BeanFactory (1)  
* Application Context (2)


New Features provided by Application Context  
* Integration with AOP  
* Message resource handling  
* Event publication  
* Aplication layer spacific contest (WebApplication Context)  


These Objects are known as __Bean__ . A Bean is a Object which is created, initiated, assambled and managed by IOC. These beans and the dependencies among then are manag reflected in Mata data.  


 ----


# __Container Overview__

ApplicationContex from org.springframework.contest is responsible for bean creation get instruction from reading metadata. This matadata can be represent by xml. java annotation and java code.  
Here you can define the objecets and interdependencies between objects. Several implimentation are avilable for ApplicationContext interface, for example __ClassPathXmlApplicationContext__ or __FileSystemXmlApplicationContext__ (XML). You can also instruct application to use java annotation or java code by using very small amount of xml. This xml can also be created by your IDE so your work is to check what is there in xml.  

> TODO-- Check what is there in very small amount of xml


## __Configuration MataData__ 


Spring container take matadata and pojo to make a bean. Spring matadata is not bind with type of matadata. it is loslly couple you can provide xml, java annotation and java code cut currently we study xml based config.  
Spring config consist atlreast one or more than one bean defination. These configuration is define in _\</bean>_ tag which came in _beans_ tag. same in java code _Bean_ annotation on method in _configuration_ mention class.  
You did not mention fine grain objects as this is responsoblity of dao or service layer to make domain layer object.  

In bean tag two attribute came  
* ID ---> name of bean  
* class ---> fully classifed class name for which you want object.  

> this ID name is for Collabrating objects.


----


## __Instantiating a Container__

Location path/s you supplied to ApplicationContext Constructor are resources string that let load metadata from external resources such as file system or class path.

> ApplicationContext ctx = new ClassPathApplicationContext("demo.xml", "services.xml");

Resource paths are used to custruct application context.


---


Let make a bean Example   
	\<beans>  
		\<bean id="obj1" class="Full Classified Path " >  
			\<property name="field name " ref="id of other bean" />  
		\</bean>  
	\</beans>  


In above mention example you can see a new tag __property__ this tag use to refer class field and name is same. this tag take two attribute name (filed name ) and ref which same as id of other bean that make a collabrating Object.  


### __Composing Xml base config__

This is difficult to have all beans in one file for large application. If we can define beans on domain basis in seprate file then is ti not good ?  
For above mention point you can give all file name in ApplicationContex cunstructor but you can also import them in one file then you can load taht file in Cunstructor using __*import*__ tag.
Import tag has one attribute __resource__ which take path of xml.

> \<import resource="path of xml file " />  

path of xml file of two type full or only name of xml file. In second case you have to make sure that file in same classpath or folder. in full path leading / remove automatically so importing file always on top. this import tag came in beans tag.  
you can also refer to parent directory using __../__ but not recommended  k


you can also use Groovy file to declare beans like   
	beans {  
	    	dataSource(BasicDataSource){  
		    url=  
		    driver=  
		    user=  
		    password=  
		   }  
		  }  
you can also use importBeans directive to import in groovy.  For Groovy implimentation for _ApplicationContext_ is __GenericGroovyApplicationContext__



## __Using Container__

Application is the interface for an advance factory capable of maintainging and registy of different beans and you can use retrive that bean from _getBean_ funciton by passing name and type.  

> DaoBean daoBean = cix.getBean("DaoBean", DaoBean.class);  

Groovy also provide different reader to load xml and groov and mix them like 

> new XmlBeanDefinitionReader(ctx).loadBeansDefination("xmls");  
> ctx.refresh();  

same for groovy GroovyBeanDefinationReader(ctx)....

---

## __Beans Overview__

Beans are created using metadata that are supplied to container. Within container these bean defination represented by _beanDefinition_ objects. which contain following metadata.  
* Fully Qualfied class name.  
* Behaviour of bean ( scope, lifecycle, callbacks and other)  
* ref to other bean that are required by bean to do it work. These are known as dependencies.  
* Other config setting require to set in new created object ( Size limit in pool or number of connections)  



### __Property of beans__  


* Class  --> name of class (full name )  
* Name  --> Name of bean   
* Scope  --> Bean Scope  
* Constructor arguments  --> Dependeny Injection  
* properties --> Dependeny Injection  
* Autowiring mode  
* Lazy initialization mode  
* initalization mode  
* destruction mode  


Other then this you can also resgister bean that are created by user using __ApplicationContaxt__ . ApplicationContext provide getBeanFactory() function that provide _DefaultListableBeanFactory_ instance in which registerSingletonor registerBeanDefination methoda are there but it is slow.   

Bean matadata and manually suply _singletone_ bean require to register as early as possible.  While overriding existing matadata  and singleton instance supported to some extent. Runtime registation is not supported for now.  


## __Nameing Beans__  


In Spring an bean can have one or more identifier and they are unique in container. Other then one identifier known as aliases.  
In xml you use _id_ and _name_ attribute (one or both ) for identifies.  
The _id_ attribute use for only one identifier which is alphanumeric by convention but you can use special char also.  
The _name_ attribute provide you power to define more then one identifier name by comma/ semicollon/ space seprated names.  
NOTE: before 3.1 id has a seprate type _xsd:id_ but after 3.1 it is xsd;String.  
you may not require to provide name or id to a bean if you did not provide name to a bean then container will provide a name, but if you want to use bean by name ref or service lookup then you required to provide name  
NOTE: Motivation for not providing name are related to using inner beans or autowirring collabraters  

> Bean nameing convention is same as java variable convention.  

These nameing convention define in _java.beans.Interospector.decapitalize_ class for generating automatic name for unname bean.

### __Aliasing a bean outside the bean defination__  
For making alias in bean you use name attribute.  
Sometime for large system it is required to provide alias name outside a bean using \<alias/> tag.  
> \<alias name=forname alias="toName" />  
NOTE: form name is bean name and to name is alias name.  
In java base config you use _@Bean_ tag for that.  


## __Instantiating Bean__

To init a bean you require class atribute, which can be provided in two ways:-    
* Container itself create a class   
* static factory method create a class. return type may bediffrent then of that class.  
* For innner bean you use binary method ( bean1$bean2)  

There are three ways to create a bean in Spripng:
* Using custroctor : This is use to create bean using class cunstructor in this option you provide id/name and class for which you require Object. IOC use that class custructor to create bean.
&emsp;&emsp; argument use are _consargs_ and _property_
* Using Static Factory Method : Static factory method is some thing where you have a staic funtion that return a Object (any type). Input in this type of bean creation are _id_, _name_, _class_ ( this is class where static function is define not the class whose object you want ) and _factoru-method_ method name which return Object.  
* Using Instance Factory Method : This is same as a static factory method way only diffrence is here method is not static so you require to provide a bean ref in place of class ( java basic) here are attribute _id_ , _name_ , _factory-bean_ (bean made by you ) and _factory-method_.  


# __Dependencies__  
 
There are two ways by which you can inject dependency  
* Constructor-based injection  
* Setter-based dependency injection  

### __Constructor-Based injection__  

In this type you have to pass argument using _constructor-arg_  attribute for cons-arg tags are:  
* _ref_ : In this you provide a ref for other bean which you are looking for as a dependency.  
* _value_ : In this you provide String value of dependency this is use in place of ref.  
* _type_ : When you pass value then it is always string so you have to provide _type_ so IOC convert it and inject in constructor.  
* _name_ : This is name of constructor perameter in case of conflict ( if both perameter are int ).  
* _index_ : This is respective position of argument required in case of conflict.  
