Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: kotlin
Topic: Delegation


---
Link:  https://kotlinlang.org/docs/delegation.html
---

The Delegation pattern has proven to good alternative for inheritance.  
Kotlin supports it's.  


In Java what is Inharitance? In Inharitance child class can override member method of parent class according to its requirement.  

To achive this in Kotlin you use __Delegation__ . In That you pass base class Impl(Parent) and then Delegation can override It.  

You required Interface in this.

```Java

interface Base {
    fun print()
}

class BaseImpl(val x: Int) : Base {
    override fun print() { print(x) }
}

class Derived(b: Base) : Base by b

fun main() {
    val b = BaseImpl(10)
    Derived(b).print()
}

```  

Delegation achive by _**by**_

---

#__Delegation Pattern__  

This is a very famous desgin pattern delegation which is used as a alternative for inheritance. Delegation means when any request came to you, you pass that request to other object in place of handling it.  

In famous books like __Desgin pattern by GOF__ and __Effective java__ it is recomended that you use composition in place of Inheritance due to below reasons.  

* Mainly classes are not desgin for inheritance as while overriding any method we did not know assumtions taken while writting those assumptions.  
* Java support delegation for multiple classes but Inharitance for one class only.  
* Delegaiton also help in segerating pronciple form Solid(Methods you requed only used by you.  
* Classes which are final are not desgin for inheritance (final) are came under delegation and in kotin all classes are final,  

you can also check Effective java Item16.  

Cons::

* Seprate interface required.  
* you can not access protected methods and properties.  

In easy language requirement of some thing(Interface ) which is implementing full fill by other class.  

##__Kotlin support for delegation__  

Kotlin provide __by__ keyword for delegation pattern support.

EG:: class <Class Name>(perameter): Interface by DelegatingClass(perameter){}

In this we are informining compiler to delegate all _Interface_ method from _mainclass_ to _DelegatingClass_  

If we have more then one interface then we can use it by seprating with __,__ and syntax is like :-

Interface1 by class1, interface2 by class2  


##__When to use Delagation and When not__ 

####USE::
* When subclass Liskov substitution principle ---  
* When all methods are not required from super class only few required.  
* When class is not desgin for substituton.  (Final, behind inteface, sum assumtion while implemention class which can be change)  

NOTE:: Liskov Substitution principle says that every subclass act as a super class( Teacher is a Employee, Peon is a Employee).  

###__Decorator Pattern__  
In Decorator pattern you add extra functaniolity in any given class and for that you use composition and add extra on that.

```Java

interface shape{
    void draw()
}

class circle implements shape{
    void draw(){
	print("Shape - circle");
    }
}

class rectangle inplements shape{
    void draw(){
	print("Shape - rectangle");
    }
}

class shape_decorator implements shape{
    Shape decorator;

    shape_decorator(Shape shape){
	this.decorator = shape
    }

    void draw(){
	decorator.draw();
    }
}

class red_shape extends shape_decorator{
    red_shape(shape shape){
	super(shape)
    }

    void draw(){
	print("color red");
	super.draw();
    }
}

```

As you saw above we shape class using decorator pattern, as we increase draw method functaniolity.  





##__Ways to achive Delegate__  
Page back. TODO

TODO:: 


Which one is better ?
