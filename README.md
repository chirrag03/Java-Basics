# Java-Basics

## Popular Java Libraries: 

### Commonly Used Java Libraries

- Utility - Collections, IO, Loggers functionlaities

- Distributed system libs - networking libs help in setting clients and servers for various protocols like http, http2, sockets.

- Akka implements the actor model of concurrency for building highly concurrent applications without headaches that concurrent modelling gives. (can distribute actors and can run on single machine also)

- Rx Java - Reactive programming . composing streams of events

- Apache camel is for connecting system to new workflows. so make integration easy

- DATA ACCESS LIBS - to get data to and from DB (relational)

- DATA PROCESSING LIBS - BIG DATA
apache hadoop - process petabytes of data on clusters running many instances of Hadoop.
Spark - used to process stream of data very fast rather than processing in batches which usually is the case with hadoop.
Both are a distributed system


### Java-based Data Processing
Machie learning libs - DL4J
can implement deep neural nets

BIG DATA STORAGE
Cassandra - DB written in java to store petabytes of data.
Neo4J - Graph DB
ElasticSearch - used to create big search indexes for big databases
HDFS - hadoop distributed file system - data processing ;layer under hadoop


## Alternative JVM Languages

### Why Alternative JVM Languages?

Other languages - these languages also give byte code and use java platform . JVM.
Reasons to use other lang - 
1) terseness
2) familiarity - python -> Jpython
ruby -> JRuby
3) use of other programming paradignms -> functional programming.

### JVM languages Groovy, Scala, and Kotlin
1) Groovy - scripting , interpreted(you can just change code reload the system to see the changes),though can be compiled also, no type system(though we can give type annotations). Works well with existing java classes. Groovy was designed to integrate seamlessly with java code.
2) Scala - Combines OO programming with functional programming, compiled lang, has type system.
Akka(for concurrency), Spark (for big data processing) written in java.
compiler may get slow due to all the features that scala has.
3) Kotlin - A "better Java". does not have a burden of backward capability that java has. SO devs took the best ideas from previous JVM languages.
provides null safety, also compiles to javascript, i.e can be run in browser. i.e can sharecode b/w browser and backend


## Useful Tools

### IDE 
eclipse , intelliJ

### Build tools 
They are used to build and manage projects. Their job comprises of managing multiple modules, managing external dependencies(download them automatically), running tests. Some build tool expect specific directory structure. 

Example of build tools - Maven and gradle.

The pom.xml will have all information (i.e. dependencies and repositories and packaging information) to build your project. A build tool gets dependencies from the repositories specified in pom.xml located in your project or settings.xml located in /.m2 directory. Then creates an executable on basis of packaging information in pom.xml, and runs unit test cases.

### CI server 
It is a server where code build and deployment happens automatically. WE tell it our git repo and after how many commits it should deploy and it automatically deploys to told ips of servers, the code that it builds . So Ci Server gets code , builds it using build tools , run tests and analyse code , deploy code. In all it is to check that you get code of a particular quality. Eg jenkins.

What is continuos integration - 
[Link for jenkins] (https://www.edureka.co/blog/what-is-jenkins/)

### Static code analysis 
Checkstyle, spotbugs. PMD - check compiled bytecode.  You tell your coding standards and programming practises to these tools and they do these analysis.
PMD(Programming Mistake Detector) is an open source static source code analyzer that reports on issues found within application code. PMD includes built-in rule sets and supports the ability to write custom rules. PMD does not report compilation errors, as it only can process well-formed source files. Issues reported by PMD are rather inefficient code, or bad programming habits, which can reduce the performance and maintainability of the program if they accumulate

E.g of tool for Static code analysis -->SonarQube - inspecting tool works with CI server and extrapolate all analyses tools

What is SonarQube - 
https://www.sonarqube.org/features/issues-tracking/
https://www.sonarqube.org/features/quality-gate/


## Summary 
1) Intro to java - JVM etc
2) Adopting java - portability , compatibility (backward), stabilty
3) Used for - From desktop apps (Swing, JavaFX) to enterprize java javaEE or jakarta EE. Shift to cloud and microframeworks in java has given rise to microframworks in modern java like spring boot.
4) Libraries for java
5) Practises and common tools - Lifecycle
6) Alternative langs - Groovy , scala, kotlin
Do Modern java action


## JAVA FUNDAMENTALS - THE JAVA LANGUAGE

1) programming lang
2) runtime environment (Config, Security, threading, I/O)-
RUNTIME ENVIRONMENT - A runtime environment, primarily implements portions of an execution model. This is not to be confused with the runtime lifecycle phase of a program, during which the runtime system is in operation. Most languages have some form of runtime system that provides an environment in which programs run. This environment may address a number of issues including the layout of application memory, how the program accesses variables, mechanisms for passing parameters between procedures, interfacing with the operating system, and otherwise. The compiler makes assumptions depending on the specific runtime system to generate correct code. Typically the runtime system will have some responsibility for setting up and managing the stack and heap, and may include features such as garbage collection, threads or other dynamic features built into the language.

Java is so flexible that there are even more runtimes than java SE provided by oracle that support same java lang.
1) Java SE - standard edition
                           - Java EE
                           - Java ME
                           - JavaFX
2) Android - very diff runtime than standard Java runtime
All these different runtimes support same Java programming language.


## Introduction and Setting up Your Environment: What Is Java

### JRE vs. JDK
JRE vs JDK
JRE is the thing needed to run the Java app on a machine (mobile, server etc)
JDK provides the tools that is needed to create the java apps which will finally run on JRE .
JRE is installed by end user
JDK is installed by developers to produce the app.
JDK installation includes JRE
xyz.java -> JDK - > Java App -> JRE -> Host environment (Mac , windows, browser , android)

(https://www.geeksforgeeks.org/differences-jdk-jre-jvm/)

-----------------------------------------
Creating a Simple App: Introducing Packages

Packages
provides organization.
follow standard naming
affect source code file structure
All lower case
Use reversed domain name to assure global uniqueness
add further thing to assure uniqueness within company
 Eg pruralsight.com -> com.pluralsight                         com.pluralsight.accounting.myProject

 com.pluralsight.courseseg.myProject
Members become part of the package - E.g Main inside com.pruralsight.myproject -> com.pluralsight.myProject.Main

Package and source file structure
Java requires no relation b/w package and code file structure BUT most IDEs require a sub folder for each part of package name.
Main inside com.pluralsight.example expects src - com - pruralsight - example - Main.java

Representing Complex Types with Classes: 
Applying Access Modifiers
A “public” class with name eg."abc" has to be inside a source file with the same name as class name i.e abc.java
NOTE - only public class. (Not inner or nested .) ……...A main method is most of the times not inside Main.java

Naming Classes
For ClassNames use PAscal case i.e Start of each word , including first , is upper case BankAccount

Method
Exiting from a Method
A method exits for one of three reason
An error occurs
 -return statement
end of method has reached
Method Return Values
return Type of Methods
A primitive value
A reference to an object
A reference to array - Arrays are objects


Applying Access Modifiers
Methods types - protected method can be called by subclasses , But private method can not be called by subclasses 
Special References: this and null

Special references - this (Allows an object to pass itself as an parameter)
null is a references literal
represents an uncreated obj
Can be assigned to any reference variable

Class Initializers and Constructors: Chaining Constructors and Constructor Visibility

Constructor - no return type

this(arg) calls constructor with one arg.
this has to be the first line of other constructor

Q- Why super and this  has to be first line ? 
Ans- The parent class' constructor needs to be called before the subclass' constructor. This will ensure that if you call any methods on the parent class in your constructor, the parent class has already been set up correctly.
As otherwise ,  in constructor you may try to access some variable of parent which has not even set

In cases where a parent class has a default constructor the call to super is inserted for you automatically by the compiler. Since every class in Java inherits from Object, objects constructor must be called somehow and it must be executed first. The automatic insertion of super() by the compiler allows this. Enforcing super to appear first, enforces that constructor bodies are executed in the correct order which would be: Object -> Parent -> Child -> ChildOfChild -> SoOnSoForth

As for why this() must run first, a constructor that calls this() skips its own super() call (since the this() call calls the super(), so we don't want to do it twice). In addition, we don't know what the arguments to super() in the this() call will be, so we need to wait for the this() call to make the super() call. In keeping with the reasoning from above, we don't want anything to execute prior to the super() call, so we can't do anything before this().

Field initialization - it is initializing any variable at the time of initializing the object, outside of any constructor.
Initialization block - code inside of a block outside of any constructor. /no matter which constructor runs this block is run as if it is first line of any constructor. if multiple initialization block they are run in order.
One constructor can call another constructor - Call must be first line

Class Initializers and Constructors: Initialization and Construction Order
Field initialization -> Initialization block -> Constructor
REMINDER - Difference b/w static block and initialization block ? 

A Closer Look at Parameters: Overloading Walkthrough
In overloading the method vs constructor it doesnt have to be the first line of the method

A Closer Look at Parameters: Variable Number of Parameters
A method can be declared to accept a varying numbers of parameter values
place an ellipse (...) after parameter type
Can only be he last type
Method receives values as an array
public void func (int a, int b, float... list) {
list .lenght() -> would work as list is an array
}
func (1, 2, 1.2) -> [1.2]
func (p1, p2, 1.3, 2.3) -> [1.3, 2,3], func (p1, p2, 1.3, 3.4, 4.5) -> [1.3, 3.4, 4.5]
All will work

A Closer Look at Parameters: Variable Number of Parameters

Summary -
Parameters are immutable (Changes made to passed value are not visible outsude of method)
Method can be declared to accept varying numb of parameter values(values received as an array, Must be last parameter)

---------------------------------

## Class Inheritance: 

### Inheritance Basics and Typed References

```java
public class BaseClass {

}
public class Derived extends BaseClass {
    public void derivedClassMethod() {

    }

}

BaseClass anInstance = new Derived();
anInstance.derivedClassMethod();
```
Doesn’t work as we can only access method that are visible to the reference type.
**NOTE -** Don’t confuse it with  overridden methods.

```java
public class BaseClass {
    public void baseclassmethod() {}
}
public class Derived extends BaseClass {

}

Derived derivedObject = new Derived();
derivedObject.baseclassmethod();
```
This is valid as the derived class has inherited things of parent .


### Member Hiding and Overriding
Member hiding: 

Overriding: If methods of same signature (Method Signature means method name and parameters.) are there in parent and derived Classes, then the method of Derived Class overrides method of BaseClass.

```java
public class BaseClass {
    int x = 10;
    public int method() {

    }
}
public class Derived extends BaseClass {
    int x = 5;
    public int method() {

    }
}

BaseClass obj = new DerivedClass();
obj.x;
obj.method();
```

If a reference type is of the BaseClass then field accessed is of BaseClass because fields of BaseClass hides the fields of derived class. This may be dangerous.
But a reference of BaseClass references object of a Derived Class then methods used are of derived class because methods are overridden.

**:bulb: So field accessed depends on reference type used whereas method depends on the constructor used i.e the type of object the reference is pointing to.**

### Object Class
Object class is base class in java. By default all classes extend this Object class.

```java
Object o = new CargoFlight();
o.add1Package(1.0, 2.5, 3.0); 		//doesnt work as o reference of Object type doesn't know addPackage.

CargoFlight cf = (CargoFlight) o;
cf.add1Package(1.0, 2.5, 3.0) 		//This runs

if (o instance of CargoFlight) {
    CargoFlight cf = (CargoFlight) o;
    cf.add1PAckage(1.9, 2.5, 3.0);
}
```

Object Methods -
clone - Create new object instance that dupliates curr instance.
hashCode - Get a hash code for the current instance
getClass - Return type info for the current instance
finalize - Handle special resource cleanup scenarious.
toString Return string of chars representing the current instance
equals - Compare another object to current instance for equality


### Equality Of Objects
```java
Flight f1 = new Flight(175);
Flight f2 = new Flight(175);
f1 == f2 	- > 	return false(as reference are checked to be equal)
f1.equals(f2) 	- >	return false(as reference are checked to be equal)
```

But now we want equal() method to behave differently. So we override it.
```java
class Flight {
    private int flightNumber;
    private char flightClass;
    
    @Override
    public boolean equals(Object o) {
        / o doesnt have access to fields of Flight as it is Object type. So we will typecase it so that it can access fields of Flight./
        Flight other = (Flight) o;
        return flightNumver == other.flightNumber && flightClass == other.flightClass;
    }
}

So now
if we do f1.equals(f2) - > returns TRUE
BUT BEWARE WHAT IF THIS HAPPENS
Passenger p = new Passenger();
f1.equals(p) - > would
return compile error as equals method would take it as an input.So we need to check the instance type before doing any typecasting.
public boolean equals(Object o) {
    if (!(o instanceof Flight)) return false;
    // rest same
}
```

### Special Reference: Super
A base class variable behaved as if it is variable of  derived class, reverse can also be done through super.

Special reference : super
Similar to this, super is an implicit reference to the current object
super treats the object as if it is an instance of its base class
Useful for accessing base class members that have been overridden.
Eg in the above implementation of equals we would like to do the logic if the references are different as if the references are same , there is no need to go for that logic . So we can use the equals method of Base class that does this.

@Override
public boolean equals (Object o ) {
if (super.equals(o)) return true;
/rest same/
}


## NOTE on Method Overriding 
Methods must have the same method signature (i.e. method name and parameters).

Method with the same signature cannot exist in the same class even with a different return type. But can exist in parent class relationship (Overriding  --- remember !). However here also the return type must be the same. (otherwise incompatible type error shown by compiler)

private methods cannot be overridden. As they can be called within the class only.


Moreover the method in the child class should not specify a lesser (weaker) access to the overriding method. (A protected method in base class cannot be overriden as private method in child class)

So method can be overridden when methods of same signature and return type and greater access is there in child class.

Also Why is greater access of overriden function allowed ? 
    Overriding method does not affect anything of overriden method of base class . as overriding function is function of an object defined as new ChildClass(). So our intention was there for overridden function to be of greater access(e.g public) . 


```java
public class JavaBasics {
   public static void main(String[] args) {
       myfunc(new Child());
   }
   public static void myfunc(Parent inp) {
       inp.md();
   }
}

class Parent {
   protected void md() {
       System.out.println("privy parent");
   }
}
class Child extends Parent {
   public void md() {
       System.out.println("privy child");
   }
}
```

Had the child class made the method private then the myFunc() would have failed.


### Class Inheritance: Using Final and Abstract

By default all classes can be extended and derived class have option to use or override (when allowed) the methods.
A class can change these default behaviours. Base class can control whether it is allowed to be extended and how overriding methods work(whether it wants to prevent overriding or require it).

1) Use "final" keyowrd 
- to prevent inheriting a class 

```java
public final class Passenger {}
```
// Now you are not allowed to inherit from this class.

- to prevent overriding a method of the class
```java
public class CargoFlight extends Flight  {
 	public final void add1Package() {
 }
}
```
This allows a class to be inherited from but does not allow a particular method to change. No point of marking method as final if class is final as you can’t override that class anyway.

2) Use abstract keyword
- to require inheriting and/or overriding

```java
public class Pilot {
private Flight currFlight;
public void fly() {
if (canAccept()){
currFlight = f;
}else {
handleCanAccept();
	}
}

private void handleCanAccept() {...}
}
```

Where is the canAccept() method ?

Our requirement is that the Class Pilot has method canAccept() but we don’t know yet what that is. // So it allows us to use that method in other method (here in fly method) .
We need to leave the implementation of canAccept() to the derived class that inherits from it.  

To achieve this we define the method as abstract in the base class.
```java
public abstract boolean canAccept (Flight f);
```

If a method is abstract, then the whole class must be abstract. So Pilot class has to be abstract.
```java
public abstract class Pilot { ...same as above }
```
NOTE - An abstract class can have both abstract and non abstract methods. Its very uncommon to have a class as abstract and method not.

```java
public class CargoOnlyPilot extends Pilot {
@Override
public boolean canAccept (Flight f) {
return f.getPassengers() == 0;
}
}
```

### Class Inheritance: Inheritance and Constructors

- Constructors are not inherited.
- A base class constructor must always be called.
- By default, no-arg constructor of the base class is called.
- Can explicitly call a base class constructor using super followed by parameter list (Must be first line of constructor).  

Lets say a constructor is called for Derived class which is not there in derived class but constructor of same signature is there in base class. But then also the constructor of base class would not be called. So if we want the same signature we will have to define the constructor in derived class with that signature.

E.g
```java
public class Flight {
    private int lfightNumber;
    public Flight() {}
    public Flight(int flightNumber) { ...
    }
}
public class CargoFlight extends Flight {
    float maxCargospace = 1000.0 f;

    1 _public Cargoflight(int flightNumber) {
        super(flightNumber);
    }

    2 _public CargoFlight(int flightNumber, float maxCargoSpace) {
        this(flightNumber);
        / we could have also called super(flightNumber ) but as this work has already been done in CargoFlight(int flightNumber) constructor we can use that only./
        this.maxCargoSpace = maxCargoSpace;
    }

    3 _public CargoFlight() {} // empty constructor

    4 _public CargoFlight(float maxCargoSpace) {
        this.maxCargoSpace = maxCargoSpace;
    }
}
```

## More About Data Types
### String Representation of Non-string Values
String - Immutable i.e any change to a string creates a new string.
- intern a string.
- String.valueOf 100 -> "100"
- toString Method


### StringBuilder Class
String is immutable whereas StringBuffer and StringBuider are mutable classes in java and provide append(), insert(), delete() and substring() methods for String manipulation.
StringBuffer has one disadvantage that all of its public methods are synchronized. Thus StringBuffer provides Thread safety but on a performance cost.
StringBuilder is not Thread safe, that's why StringBuilder is faster than StringBuffer.
- For best performance pre sized buffer . Will grow automatically if needed
- Use toString to extract resulting string
```java
StringBuilder sb = new String StringBuilder(40);
sb.append("I flew to ");
sb.insert(9, " st ")
String message = sb.toString();

```
Note: String concat + operator internally uses StringBuffer or StringBuilder class.

### Primitive Wrapper Classes and Type Conversions
Primitive wrapper Classes - wrappers for primitive objects .
- Boolean
- Number(Byte, Short, Integer, Long Float, Double)
- Character
ALL WRAPPER CLASSES ARE IMMUTABLE. So a given instance always has the same value inside of it. So if you have a reference to instance of a primitive wrapper classes and you do something to change the value, you would get a reference to a different instance of that class.
We often need to convert primitive to Wrapper class object. Java provides a number of ways to handle conversions.Common conversions handled automatically.

Integer a = 100; 100 -> primitive ; a -> reference of Integer type , java take care of making a object with value 100;
int b = a; b -> primitive int; java will take care of taking 100 out a and put it to b;
Integer c = b;

- WRAPPER classes provide methods for explicit conversions.
 1) Primitive to wrapper ( method called "ValueOf") this idea is called boxing.
 2) Wrapper to primitive (method called "xxxValue") where "xxx" is the primitive value type. e.g intValue, doubleValue etc. this is called unboxing
 
```java
Integer d = Integer.valueOf(100);
int e = d.intValue();
Integer f = Integer.valueOf(e);
Integer a = 100; and Integer d = Integer.valueOf(100) are doing the same thing.
```

### Using Primitive Wrapper Classes
Using Wrapper Classes
Object[] stuff = new Object[3];
stuff[0] = new Flight(); stuff[1] = 100; (this can be done due to auto boxing of java);
and also rather than having checks on primitive types for something to just check the setting of a variable is not straight forward.
E.g
int flightNumber;
if (flightNumber > 0) do something
Now we can do
Integer flightNumber;
if (flightNumber != null) do something;
There are many other members in wrapper classes.
MIN_VALUEm MAX_VALUE, isLetter , isDigit etc


### Wrapper Class Equality
```java
Integer a = 1000; Integer b = 1000
a == b -> false ; a.equals(b) -> true;
Integer a = 4 2, b = 2 2 * 2;
a == b True;
```
Why is this happening ?
in JAVA there are Boxing converisions that return the same wrapper class instance
1) int, short , byte from -128 to 127
2) char . from '\u0000' to '\u00ff'
3) boolean true false;
So we get the same exact instance for same exact value for values b/w these.


### Final Fields and Enumeration Types
Making a field final prevents it from being changed once assigned.
1) A simple non-static final field must be set during creation of an object instance. (Can be set with field initializer, initialization block, or constructor).
2) Adding the static modifier makes a final field a named constant.

ASIDES START  
- Fields defined in an interface are static and final by default but in abstract class you can define non static object fields.

**Why are all fields in an interface are static and final ?**  
Because no object can be created, thus fields must be static. We need that value or capability is there.
All methods & fields in the interface are public Why? because the motive of an interface is to provide the user a set of fields and methods.
It makes no sense to make fields private or protected.
ASIDES END


### ENUMERATION Types

Enumeration types useful for defining a type with a finite list of valid values.
- Declare with enum keyword
- Provide a comma separated value list.

```java
public enum FlightCrewJob {
    Pilot,
    Copilot,
    FlightAttendent,
    AirMarshal
}
public class CrewMember {
    private FlightCrewJob job;
    public CreMember(FlightCrewJob job) {
        this.job = job;
    }
    public void setJob(FLightCrewJob job) {
        this.job = job;
    }
}
CrewMember judy = new CrewMember(FLightCrewJob.CoPilot);
judy.setJob(FlightCreJob.Pilot);
```

### More About Data Types: Summary
String class stores an immutable sequence of Unicode characters
 ** Implement toString method to
 provide conversion to a string .
StringBuilder class provides an efficient way to manipulate string values.
Primitive wrapper classes bring class capabilities to primitive values .
 **Wrapper classes much less efficient than primitive types.
Final fields prevent a value from being changed once assigned
 ** Non-static final fields must be set during object instance creation.** Static final fields act as named constants
Enumeration types useful for defining a type with a finite list of values.


## Exceptions and Error Handling: Error Handling with Exceptions

Error handling needs to be implicit in application development.
The traditional approach of checking error codes / flags is too intrusive

Whenever there is some error, an error object is created by JVM and is thrown. Now what should happen, should the program continue to run or should it give programmers a choice , whether to continue running programme, or stop the execution. 

To give programmers a choice java platform provides exceptions. 

Exceptions provides a non intrusive way to signal errors
Any code can throw an exception: your code, code from a package written by someone else such as the packages that come with the Java platform, or the Java runtime environment. Regardless of what throws the exception, it's always thrown with the throw statement.


**ERROR vs EXCEPTIONS**  
Both Errors and Exceptions are the subclasses of java.lang.Throwable class. 

An Error “indicates serious problems that a reasonable application should not try to catch.” Errors are the conditions which cannot get recovered by any handling techniques. It surely cause termination of the program abnormally. Errors belong to unchecked type and mostly occur at runtime.  
Eg: Stack overflow error in case of infinite recursion, Out of memory error in case of exhausting the heap space .  

If these cases occur, program cannot continue the execution i.e it will have to terminate and hence JVM throws Throwable object of type Error.

An Exception “indicates conditions that a reasonable application might want to catch.” Exceptions are the conditions that may occur at runtime or compile time and may cause the termination of program. But they are recoverable using try, catch and throw keywords. 

Exceptions are divided into two categories : checked and unchecked exceptions. Checked exceptions like IOException are exceptions which compiler necessitates to be catched if thrown in code .
While unchecked exceptions like ArrayIndexOutOfBoundException, ClassCast , Null Pointer  WILL NOT BE CHECKED BY  THE compiler (even if you throw the exception explicitly). It is mostly caused by a program written by the programmer.


try/catch/finally provides a structured way to handle exceptions.
1) the try block contains the "normal" code to execute
Block executes to completion unless an exception is thrown

2) The catch block contains the error handling code .
Block executes only if matching exception is thrown

3) The finally block contains cleanup code if needed
Runs in all cases, following try or catch block

      Error Handling example
C:\Numbers.txt;
5
12
6
4
A lot of things may go wrong here. May be the file doesn’t exist, May be some kind of system error occurred , When we try to read from the file, May be there is bad data in the file, May be there is bad data (there may be "xyz" n place of number)
So that is why we put everything in a try block;

Whenever we open a file we should be closing it, irrespective of the fact that exception occurred or not. So i.e why we close it in a finally statement to make reader.close();

```java
BufferReader reader = null;
int total = 0;

try {
reader = new BufferReader (new FileReader("C:\Numbers.txt"));
String line = null;
while ((line = reader.readLine()) != null) total += Integer.valueOf(line);
System.out(println("Total: ) + total);
} catch {
System.out.println(e.getMessage());
} finally {
try {
// it may be that reader is not defined i.e in error occured in File reading itself. So we put null check there.
if (reader != null){
reader.close();
} catch {
System.out.println(e.getMessage());
}
}
```

### Handling Exceptions by Type

For an object to be able to be thrown , it needs to extend class called "Throwable".
Classes which extend throwable
1) Error - it throws JVM related errors. E.g LinkageErrors. These errors are unchecked (i.e compiler does not require them to be handled.)
2) Exception - Includes
a. RuntimeException -  this includes exceptions like NullPointerException, ArrayIndexOutOfBound , ClassCastException  and others . runtime Exception class extends Exception class. It is made for the use cases where we want to terminate the thread by throwing an exception. So we can make a custom exception extending RuntimeException and if we throw it, the compiler does not require us to catch it . So At runtime when it will be thrown , thread will terminate.
These are also unchecked exceptions.
b. Other exceptions extending class Exception. These include exceptions like IOException.
ONLY EXCEPTIONS WHICH EXTENDS "Exception" CLASS ARE CHECKED EXCEPTIONS. i.e compiler wants them to be handled before hand in code.
SO ALL EXCEPTIONS extending "Exception" class are checked exceptions except RuntimeException class (which include NullPointerExeption).

Typed Exceptions
Exception can be handled by type.. i.e Each exception type can have a seperate catch block and they are tested in order and first assignable catch is selected.


### Exceptions and Methods
**How try catch works?**
When a method has try catch block it puts a marker on the call stack. So if an exception occurs the method with a marker is checked on the call stack, control is passed to that method, thus removing all other method calls from the call stack.

So Exceptions propagate down the call stack. (Can cross method boundaries)
Exception are part of a method's contract i.e Method is responsible for any checked exceptions that might occur. It has 2 ways to deal with it .
1) Catch the exception
2) intimate or Document that the exception might occur by use of "throws" clause.

For e.g if we are using FileReader(filename) and reader.readline() in our code. They may throw an exception. So we don’t put try catch in our code as those should be handled by FileReader and realine only. So instead we put the "throws" clause. And Since FileReader says it throws "FileNotFound Exception" and Readline throws "IOException". and FileNotFoundException is also an IOException, we can throw IOException.
IF WE DIDN’T "CATCH" OR DIDN’T PUT THE "throws" on , COMPILER WOULD ACTUALLY COMPLAIN. So by putting the "throws" we say its our responsibility in dealing with it.


```java
try {
....
} finally {
if (reader != null) {
reader.close();
}
}
```

// Here if everything runs fine, finally runs and reader close. and if exception occurs finally still runs and close the file and let the exception call up the call stack.

### Exceptions and Methods
The throws clause of an overriding method must be compatible with the throws clause of the overridden method.
Ways to change the throws clause in the overriding method (i.e. in derived class):
1) Not providing any throws clause. (i.e we don't throw any exception that is not already defined in base class.)
2) Can throw the same exception as base class.
3) Can throw a derived exception

WHY SO : -1
Checked exceptions are intended for use in situations where a method may expect its caller to be prepared to deal with certain problems that may arise. If callers of BaseFoo.Bar() are not required to deal with a FnordException, then method DerivedFoo.Bar() cannot expect its callers to deal with a FnordException either (since many of its callers will be the same ones that were unprepared to have BaseFoo.Bar() throw it).

### Throwing Exceptions and Custom Exceptions
Throwing Exceptions
we can also throw exceptions to signal that error has occurred or we want to add more information about error that has occurred.
they are thrown with throw keyword.
Must create exception instance before throwing. Be sure to provide meaningful detail.
Most exception classes provide a constructor that accepts a String message or other detail
Now there are cases where we make new exception on top of some other exception to add some info. (tying one exception to another exception).
So when caused by another exception include originating exception
All exception classes support initCause method to associate one exception with other.
Many provide a constructor that accepts the originating exception.


### CalcEngine with Exceptions
```java
try {
    helper.process(statements);
} catch (InvalidStatementException e) {
    if (e.getCause() != null)
        print("Original exception: " + e.getCause().getMessage());
}
public void process throws invalidStatementException() {
    // FIRST THROW
    if (someArray.length != 3)
        throw new invalidStatementException("Incorrect no of fields", statement);
}


try {
    leftVal = something;
    rightVal = something;
} catch (NumberFormatException e) {
    // SECOND THROW
    throw new InvalidStatementException("Non numerc data", statement, e);
}


public class InvalidtatementException extends Exception {
    public InvalidStatementException(String reason, String statement) {
        super(reason + ": " + statement);
    }
    public InvalidStateentException(string reason, String statement, Throwable cause) {
        super(reason + ": " + statement, cause);
    }
}
```

Exceptions and Error Handling: Summary
1) Exceptions provide a non-intrusive way to signal errors
2) try/catch/finally provide a structured way to handle exceptions
3) Exceptions are caught by type
- Can have seperate catch statement for differing exception types
- Catch from most specific to least
4) raise exceptions using throw
5) Methods must declare any unhandled checked exceptions using throw
6) Can create custom exception types
Normally inherit from Exception












