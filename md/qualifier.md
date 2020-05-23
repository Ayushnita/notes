__Qualifier Annotation__

In Spring Autowire work on type and suppose if you make two bean of same type (you can ) but by diffrent name then spring came in cofusion that which one I have to pich you then using
__Qualifier__ annotation ` _you_ ` tell spring to use which bean.  

'''xml

	<bean name="a" class="A">
		<property name="name" value="Ayush"/>
	</bean>
	<bean name="b" class="A">
		<property name="name" value="Ayush Agrawal"/>
	</bean>


'''  


Now while autowiring you provide name of bean using Qualifier annotation

'''java

	@Autowire
	@Qualifier("a")
	A a ;

'''  

NOTE :: if you did not provide it throw an Error :

'''java 

	No Unique bean of type A ...

'''  


