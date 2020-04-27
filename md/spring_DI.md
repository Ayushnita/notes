# __Spring DI__  

This notes are from a vide which came in 2012 [ Spring Dependency Styles](https://www.youtube.com/watch?v=dJh84cjMY3E) by Chris Beams    
For origional slide check [github](https://github.com/cbeams/distyles/blob/master/slides/slides.md) or you can also find code here,  
this notes is only for my way of understanding.  


## __What a dependency Injection__  

Let we start from a code example   

@@@java  

	public class A {  

	    // A require a object of Employee class  
	   // Object created ....  
	   Employee e = ....  
	   // Object crreated 
	   System.out.println(e.getInfo("122"); // id provided as input. 

So here the point is how to create a Object:  
* _new_ keyword.  
* factoryMethod  
* JNDI lookup  

All above mention styles you are creating object in code due to which you always depend on that object.  
you never provide type of objects for diffrent environment like for test, qa, qa2 etc.  
So how we remove dependency of Employee from class A. Sol: if we pass that dependency in constructor or in setter then from you set this value so now you can pass any thing from outside and this is DI.  

@@@java   

	A(Employee e){  
	    this.e = e;  
	}  


This is only dependency injection but when we do this why we require spring because spring provide more and DI by default.  
let consider we start using this then in main class I have to make a Employee object and then pass that in A class, then require to do same in unit test main class. and if we have more then one
environment then we require more same type of code or make a factory for that. Spring provide factory (IOC) for that.  
Spring container is only factory you require.  

## __Ways to provide DI in spring__   

* Xml -- came in spring 1.0  
* xml + namespaces -- came in spring 2.0 --> spring name spaces reduce boider plate for trxn, aop, security and other thing.  
* annotation  -- @Component or @Autowire use to make a class as a bean and inject it other class but still require to mention namespace in xml ' component-scan '  
* Java config -- this is no xml state in which you meke <beans> wy annotating class with @Configuration or <ben/> with @bean annotation on method. 
	* while loading context require to use AnnotationSpringApplicationContext  
	* decentralize  
	* if anythig change require to compile again  
	* type safe  
* Hybrid (recomended) use mix as per requirement.  
