# __Spring Configuration Setup__  

## __@PropertySource__  

* This is use to set spring properties from a spacific file ( not fix application.yaml) to load in spring environment .  
* you can use @Value or spring _Environment_ class to bind this properties.  
	* Spring @Value example  
	'''java  

		@Value("${thread.count}")  
		private int value;  
	'''  

	* Using Environment    
	''' java  
		
		@Autowired  
		Environment env;  

		public A(){  
		    threadCount = env.getProperty("thread.count");  
		}  

	'''  

* In PropertySource annotation you have to provide config file path.  
	* EG 1:  
	'''java  
		@PropertySource("classpath://config.yaml")  
	'''  

	* EG 2:  
	'''java  
		@PropertySource("file://{$app.home}/app.yaml")  
	'''  
	
	In above mention Example you use one property _app.home_ to set path of propoerty file.  

* Provide Multiple Property File  

	''' java   

		@PropertySource({  
		    "classpath://path1",  
		    "classpath://path2"  
		})  

	NOTE:: if any prperty present in both file then it is override by secondone.  

* In spring4 they introduces __@PropertieSources__ take care of extra s in end this is for supporting JAVA8.  

	''' java  
		@PropertySources(  
			@PropertySource(),  
			@PropertySource()  
			
			)
	'''

* Let if property file is not present then you want that it will be get ignorred you have to add one more flag _ignoreresourseNotFound=true_ in __PrepertySource__ annotation.  
:
