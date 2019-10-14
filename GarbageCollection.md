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


### Different Types of Garbage Collection
There are different types of GARBAGE COLLECTORS -
**1) Do nothing** - not freeing any memory. Just guarenting that no live objects will be reclaimed.

**2) Reference Counting** - for a variable two functions - 
    1) addReference - increment reference count . 
    2) release - decrements reference count . When reference count reaches zero. Object can clean itself up.
In this we’ll not be able to delete cyclic references.

**3) Mark and sweep** - Has 2 phases .. a) Mark phase walks through all live memory marking it alive and sweep phase removes all unused memory.
this leads us to memory which can be fragmented.
Compaction is done by rearranging the marked memory.

**4) Copying** - Work hand in hand with mark and sweep garbage collection. Marked objects are copied to a buffer (new space) before sweep phase runs on the old space, hence the memory is no longer fragmented.

**5) Generational** - if an object survives one GC , then GC would not look at it again for a while. This improves performance of GC.

**6) Incremental** - does not look at all the memory all the time during Garbage collect. so kinda like Generational.

SO GC are of many types. So we tend to have a mixture of all these.
