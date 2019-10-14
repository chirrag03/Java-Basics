# Garbage Collection

## Introduction 

We learn how to interact with JVM externally i.e using tools given by JVM or internally using some classes provided by JVM.  

### Why GC?
Imagine,  
> Account acc = new Account();  
The question will arise who will delete this object? Creator or user?  

**1) CREATE AND FORGET:**  
No need to remember to delete. GC will do it. We don't need to free the memory as in C++ and C.  

**2) USE AND FORGET:**  
No need to ask "Should I delete ?"  

> Account acc = getAccount();  
Thus either the receiver or the giver of acc object can delete i.e the class that implements getAccount()  

If neither deletes it -> memory leak  
In C++ the method who is getting this object need to free the memory, so the user of object need to have in mind when to delete object but in java the user does not need to think about object freeing while using an object
If both delete it -> null pointer exception somewhere else which will be very hard to track.  

**3) USE WITH CONFIDENCE:**   
Objects will not vanish or corrupt behind your back. In C++ some other thread may delete the object which will create null ptr exception later.

### GC PROMISE  
- Claim no live objects  
- No promise about dead objects.  
So dead objects may be present in memory. BUT no live object will be deleted or reclaimed. 
We don't know when GC will run, whether it will run before our application ends or not.


### Different Types of Garbage Collection
There are different types of GARBAGE COLLECTORS -  
**1) Do nothing** - Not freeing any memory. Just guarenting that no live objects will be reclaimed.

**2) Reference Counting** - for a variable two functions - 
    - addReference - increment reference count. 
    - release - decrements reference count. 
When reference count reaches zero, object can clean itself up. In this we’ll not be able to delete cyclic references.

**3) Mark and sweep** - Has 2 phases ....Mark phase walks through all live memory marking it alive and sweep phase removes all unused memory. This leads us to memory which can be fragmented. Compaction is done by rearranging the marked memory.

**4) Copying** - Work hand in hand with mark and sweep garbage collection. Marked objects are copied to a buffer (new space) before sweep phase runs on the old space, hence the memory is no longer fragmented.

**5) Generational** - If an object survives one GC, then GC would not look at it again for a while. This improves performance of GC.

**6) Incremental** - Does not look at all the memory all the time during Garbage collect. so kinda like Generational.

So GC are of many types. So we tend to have a mixture of all these.  

Now let's have a look at some of these in detail.  

### Reference Counted Garbage Collection
In reference counting, we have a problem of circular references where an object1 references object 2 and object2 also references object1 and they have no external reference. This is also known as Island of Isolation.  
These cyclic references won't be removed, although there is no reference that can be used to access these objects.

### Mark and Sweep GCs

Typically 3 phases -  
**MARK** - Identifying objects still in use.
Start from the root set and following other references from nodes of memory, GC mark the live memory.
In case of cycle in memory and not reference from root set .. No problem because we’ll not be able to reach that cycle as no external references.

![noImage](./img/MarkAndSweep1.png)

![noImage](./img/MarkAndSweep2.png)

**SWEEP** - Removes unused objects.

![noImage](./img/MarkAndSweep3.png)

**COMPACT** - To compact the memory. So physical addresses of memory changed. a references rearranged accordingly in root set
In java we don't have physical addresses of memory. Objects internally manages them.

![noImage](./img/MarkAndSweep4.png)


### Copying GCs 

Things are a little different.
When memory for a buffer gets full. GC run and mark live memory.

![noImage](./img/CopyingGC1.png)

Then it copies it to other buffer and rearranges references in root set.

![noImage](./img/CopyingGC2.png)

Then removes dead memory from previous memory.

![noImage](./img/CopyingGC3.png)

After the copy and compaction, we end up with a compacted copy of the data in new space data and a (hopefully) large, contiguous area of memory in new space in which we can quickly and easily allocate new objects.
The next time we do garbage collection (i.e when the space in which we are allocating memory from now gets full), the roles of old space (from space) and new space (to space) will be reversed.


### Generational GCs

GENERATIONAL COLLECTORS
There are different generations - Younger , older.  
Idea is once an object survives one GC. it is promoted to a different generation.  
And GC will sweep through the younger generation more often than the older generation.  


Let's see how thihs happens:  
So in young generation we have allocated memory. We have old generation, where there maybe alive maynot be alive.
Once GC runs, the survivors of that are moved to old generation.

![noImage](./img/GenerationalGC1.png)

![noImage](./img/GenerationalGC2.png)


And diff environment have diff number of generations. 
Java has two: Young and old generations.
.Net has three.










