#__AutoConfigure__  

There is a jar springboot.autoconfigure   
In above mention jar META-INF is a folder in which all configuration are there or path of jar which contain config.  
There are many config class  

There are annotation @Conditional.... present on each class  
It reads  .properties file from hardcoded path  
Also read spring.factory  
Auto register with @PropertySource  

### From where it read properties  
* Command line argument
* Jar file
* property file  

---

@ConditionalOnXXX are there from which you can figure which configuration work  

@ConditionalOnBean
@ConditionalOnClass

you can also achive this by implementing __Condition__ interface and then use it in __@conditional__ annotation  



#__Sterio Type Annotation__

@Component  
@Repository  
@Service  
@Controller  


#__AutoWired__

@autowired  
@autowired(required=false)
@qualifier("xxxxx")  


---
#__Bean Life Cycle__  

NOTE:: Important   

This is for any java application
* @PostConstruct
* @PreDestroy


This is for Spring run after constructor  
* initMethod
* destroyMethod



