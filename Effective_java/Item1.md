Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: Effective_java
Topic: Creating and Destroying Objects  


---

# Consider Static Factory Mehod in place of Constructors   

There is very Simple way to create a Object in java which is __new__ keyword, lets understand how this keyword is going to work for you. __new__ keyword call constructor of class according to perameters.   

In above approch there are few issues.  
* Name of all constructor are same and that must be the name of class.  
* Every time you call, you get a new Object.  
* You can only return Object of smae class, no sub class came in considiration.  
* Class required to exist in your framework, implementaion can not be passed to client class.  


Lets Explain point 3 and 4 here   

Point 3:  

In point 3 I am trying to say that you can return any sub type on the basis of input and this also help to make classes non public just requred to create on Non-Iniciated class that will return Other class Object. Like java Collections class (utils one)    

In Point 4, I am taking a service Provider framework (TODO)   

CONS::   

Require to document propoerly.  
Classes with public and protected class will not be sub-classes.   


''' Java   

public static Type getInstance(perameters){
    // create a new class or use pre creted one   

    return type;
}


'''




