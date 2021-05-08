# __Java Reference__   

There are mainly four type of Java reference  
* Strong  
* Weak  
* Soft  
* Phantom   

## __Strong__   

This is created when you create a new Object.  

## __Weak__  
This reference can be collected by java GC.  

MainlyUse in WeakHashMap, you can also create them useing WeakReference<ClassA> .   


## __Soft__   
This ref is not elegible until OOM occues or you can say Major GC.  

SoftReference  

## __Phantom__ 

This is a Object which is available for garbage collection but one difference before moving it make a ref for that and put in a queue.  

