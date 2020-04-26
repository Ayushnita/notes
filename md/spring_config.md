# __Spring Config__   

These notes are make form a video on [Spring Tips: Configuration](https://www.youtube.com/watch?v=PsNNGuLi0ns) by joshlong  

##  __General Info__   



* By default we have a config file known as application.yaml  
* you can also change properties file by using command line arguiment _spring.config.name_  , here you provide file name   
* Environment is a  class in spring in which all properties load and using getProperty() method you can get their value   
* There is an another way @value in argument from where you can provide value and also assign default value in this.  
* ${} this syntax can also be use in property file.  
* you can load properties from diffrent location   
	* property File  
	* environment Variable  
	* commandline peramenters  
	* profile based properties file  
	* config server ( discuss after we learn config server )   
	* You can also provide custom properties source ( like db and other things)   


## __Custom Properties Source__  

* Create a class Extent it with PropertySource<String>  
* constructor  
* override  _getProperty(Strign name)_  
* Till now you create config source but how to provide this to spring two ways:  
	* Before ctx load :   
	''' new springconfigbuilder()  
		.source(mainclassname.class)  
		.initlizers(applicationCtx -> ctx.getPropertiesSources().addLast(className.class)  
		.run(args();  
	'''   
	* After application start using autowire  
	'''  
		public setExternalConfig(ConfigurableEnvironment configEnvironment){  
		    configEnvironment.getAllProperties().setLast(className.class);  
		}  
	'''  


## __Bind Property to Class__   

* To bind propertie in a class at compile time you use some configuration  
* make a class you are looking to wind   
* annotate that class with _@configurationProperties("baseName)_  
* annotate main class with @EnableConfigurationProperties(ClassName.class)   
* done   


## __SpringConfigServer__  
* Here we discuss very little.  
* First setup config server  
* _@EnableConfigserver_ annotation on main class  
* provide git url   
* Make a client application  
* make a new config file bootstrap.properties  
* provide git url / file path   
* property file name in must be same as application_name.properties   


## __Spring Vault__

* vault is like a db which you run saperatlly  
* Then in application you provide VAULT_TOKEN ( if possible using environment variable)  
* Then provide spring.cloud.vault.schema  

