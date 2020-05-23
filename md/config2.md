# __Making you own Config__  

---

In Spring there are lot of config avilable and you can use them to configure them as per you requirement but suppose, if you required to make you own config that can be tuned by client for its
own requirement, thats good but HOW?  

Spring provide a way in which you expose class feilds as a config property and configure tem from spring config. That is possible using __ConfigurationProperties()__ annotation and you can
provide prifix for that. This is a class leavel annotation.  

'''java  
	
	@ConfigurationProperties(prifix="ayush.default")  
	classs AyushConfig{  

	    private int a;  

	   }  

'''  

Now you can set it from config file using _ayush.default.a = 10_ , But still not fully in control I want to put validation on it. It is as putting validation on other class feild using
__Validated__ annotation on class.  

''' java  

@ConfigurationProperties(prefix="ayush")  
@Validated  

class A{  

    @Min()  
    @Max()  
    private int a;  
}  

'''  

but still one issue if you use it in IDE it show a warning and no help for this configuration which is not a good Idea for client point od view so I want some help section also avilable for
this type of config, This is also possible by providing metadata about this config.  

To add metadata for configuration you have to provide details about config in _/src/main/resources/additional-spring-config-metadata.json_ file. Format for metadata is mention below.    

''' json  

{  

	"properties": [  

			{  

				"name": "taco.orders.page-size",  

				"type": "java.lang.String",  
  
				"description":  

					"Sets the maximum number of orders to display in a list."  

			}  

		]  
}  

'''  

in above mention config there are 4 things ::  

* properties: --> Array that contain all properties list or you can say it is a root element of json.  
* name --> Name of property.  
* type --> Type of propery  
* description --> Description for property, like help section.  




