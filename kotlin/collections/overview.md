Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: kotlin/collections
Topic: colleciton 

---

---

##Collection Type  

* List  
	* access by index.  
	* can repet  
	* position matter

* Set  
	* No duplicate  
	* No order  
	* Not access by position.  

* Map  
	* Key-value pair  
	* key unique 
	* One null key  


---

There are two type of interface for each collection type in kotlin.  
* Read only  
* Mutable  

Read only interface provide operation for accessing only but in mutable you can do all type of operation on them.  

NOTE:: to asign a mutable interface did not require var as the refrence did not changing only data manuplating but you can not reasign that variablewith new collection.  

```kotlin 
val number = mutableListOf("one", "two")
number.add("three")  //fine

number = mutableListOf("ten", "nine") // not work compile time error
```



