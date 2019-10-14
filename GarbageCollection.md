# Garbage Collection

## Introduction 

We learn how to interact with JVM externally i.e using tools given by JVM or internally using some classes provided by JVM.  

### Why GC?
Imagine,  
> Account acc = new Account();
The question will arise who will delete this object? Creator or user?  

**1) CREATE AND FORGET:** no need to remember to delete. GC will do it
we don't need to free the memory as in C++ and C.  

**2) USE AND FORGET:** no need to ask "Should I delete ?"  

> Account acc = getAccount();
Thus either the receiver or the given of acc object can delete i.e the class that implements getAccount()  

if neither deletes it -> memory leak  
In C++ the method who is getting this object need to free the memory, so the user of object need to have in mind when to delete   object but in java the user does not need to think about object freeing while using an object
If both delete it -> null pointer exception somewhere else which will be very hard to track.  

**3) USE WITH CONFIDENCE:** objects will not vanish or corrupt behind your back
In C++ some other thread may delete the object which will create null ptr exception later.

THE GC PROMISE  
--> Claim no live objects  
  - no promise about dead objects.  
So dead objects may be present in memory. BUT no live object will be deleted or reclaimed. 
We don't know when GC will run, whether it will run before our application ends or not.
