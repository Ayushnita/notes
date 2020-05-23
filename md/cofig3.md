# __Profiles__  

---

In Application devlopent it is import to test up your code before deploy ing in production so that if there is any issue we will catch it before going in production, for that we test our
application in diffrent environment ( like dev, qa, etc).  

While adding diffrent environment we have required to add some environment specific beans or properties depending on which environment you are working as you are did not want to use prod db for
qa envirnment.  

so to acchive this spring introduce __Profiles__, profiles are nothing you can say environemnt specific property file. if you make any file application-{ENV}.yaml then automatically spring
assume that config file will we load only in {EVV} profile and application.yaml will we active only in default profile ( noting is provided ). This is about file what about Beans and config
classes.  

Spring also provide __@Profile__ annotation whic you can apply on Method (Bean) or class(Config Class) to specify in which profile they load in application contxt.  

Here we set all thing how to make beans and properties profile specific, but not to tell spplication which profile to use in which environment becase if did not tell then it will always use
default profile  

To tell application which profile to use you set _spring.profiles.active_  property. donot set in config file otherwise it become default profile provide it using System , Environment or java
argument.  

Some example of profile annotation:  

''' java 

	@Profile("dev")
	@Profile("!prod)

'''

For tests you can use __@ActiveProfile__ annotation.  
