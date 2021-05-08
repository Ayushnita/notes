Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: kotlin
Topic: Delegation Propoerties


---
Link: https://play.kotlinlang.org/byExample/07_Delegation/02_DelegatedProperties
	https://kotlinlang.org/docs/delegated-properties.html

---


#Propoerty Delegation.  

In Kotlin you can understand delegation as some is full filling requirement of someoen.  

```Kotlin 

class AImpl: A by B

```

In above example AImpl required to implement all methods of A Intefrace but now due to delegation A can use all methods of B as Its own so _B_ methods are now as it _AImpl_ methods, this is delegation.  

Same happen with propoerty delegation in kotlin every peoperty have mainly two functions, __set__ and __get__, when you use delegation, delegated class provide implementation for that and there you may log or check you requirement. Make your class simple and different logics stays seprate.  

The class which provide property delegation required to have these two methods. 
* setValue(thisRef: Any?, property: KPropoerty<*>, user: User)
* getValue(thisRef: Any?, propoert: KPropoerty<*>): User

__thisRef__ is like reference to context where tis propoerty is mainly for Android. you want that get method for this propoery only work in Activity not anywhere else.  

__propoerty__ this is propoerty metadata.  

__user__ value to set/get.  

##Predefine Delegates  

####Lazy Delegarte  

In this delgate as name suggest value assign only when it use first time.This is only applicable on val(READ ONLY).  

```Kotlin 

val user: User by lazy(){User()}

```

in above example value of _user_ property assign only when it is call first due to delegation.  

this lazy is thread safe by default, if you want to make it fast and non thread safe use _LazyThreadSafetyMode.NONE_ as a lazy funtion perameter.  

```kotlin

val user: User by lazy(_LazyThreadSafetyMode.NONE_){User()}

```

* Provide class initlization so app open fast.  
* Some value never used so never initlized.  

