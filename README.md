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
## Introducing Packages
- Provides organization.
- Follows standard naming
- Affect source code file structure
- All lower case

- Use reversed domain name to assure global uniqueness  
> Eg: pruralsight.com -> com.pluralsight    

- add further thing to assure uniqueness within company
> Eg: com.pluralsight.accounting.myProject
> Eg: com.pluralsight.courseseg.myProject

Members become a part of the package  
> E.g Main class inside com.pruralsight.myproject -> com.pluralsight.myProject.Main

**Package and source file structure**  
Java requires no relation b/w package and code file structure BUT most IDEs require a sub folder for each part of the package name.
A class Main inside *com.pluralsight.example* expects *src -> com -> pruralsight -> example -> Main.java*


## Representing Complex Types with Classes: 
### Applying Access Modifiers
A “public” class with name eg."abc" has to be inside a source file with the same name as class name i.e abc.java
NOTE - only public class (Not inner or nested)

### Naming Classes
For ClassNames use Pascal case i.e Start of each word, including first, is upper case. Eg: BankAccount

### Method
**Exiting from a Method**  
A method exits for one of three reason
- An error occurs
- return statement
- end of method has reached

**Method Return Values**  
return Type of Methods
- A primitive value
- A reference to an object
- A reference to array - Arrays are objects  

**Applying Access Modifiers**  
Following access modifiers can be used:
- private : can be accessed within a class only
- protected : can be accessed within a package or from subclasses 
- package-private : can be accessed within a package
- public : can be accessed form everywhere

| Access Modifiers        |                                   | 
| ----------------------- |-----------------------------------| 
| private                 |within a class only                |
| protected               |within a package or from subclasses|
| package-private         |within a package                   |
| public                  |everywhere                         |


**Special References: this and null**  
*this* (Allows an object to pass itself as an parameter)  
*null* is a references literal that represents an uncreated obj. Can be assigned to any reference variable.  

## Class Initializers and Constructors

### Chaining Constructors and Constructor Visibility
Constructor - no return type

this(arg) calls constructor with one arg.
this has to be the first line of other constructor

**Q- Why super and this has to be first line :question:**  
The parent class constructor needs to be called before the subclass constructor. This will ensure that if you call any methods on the parent class in your constructor, the parent class has already been set up correctly. As otherwise, in constructor you may try to access some variable of parent which has not been set.  

**_In cases where a parent class has a default constructor the call to super is inserted for you automatically by the compiler. Since every class in Java inherits from Object, objects constructor must be called somehow and it must be executed first. The automatic insertion of super() by the compiler allows this. Enforcing super to appear first, enforces that constructor bodies are executed in the correct order which would be: Object -> Parent -> Child -> ChildOfChild -> SoOnSoForth_**

**As for why this() must run first,** a constructor that calls this() skips its own super() call (since the this() call calls the super(), so we don't want to do it twice). In addition, we don't know what the arguments to super() in the this() call will be, so we need to wait for the this() call to make the super() call. In keeping with the reasoning from above, we don't want anything to execute prior to the super() call, so we can't do anything before this().

### Field Initialization 
It is initializing any variable at the time of initializing the object, outside of any constructor.  

### Initialization block 
Code inside of a block outside of any constructor. No matter which constructor runs, this block is executed as if it is the first line of any constructor. If multiple initialization blocks are present, then they are run in order.  

One constructor can call another constructor - Call must be first line

### Initialization and Construction Order
Field initialization -> Initialization block -> Constructor  

REMINDER - Difference b/w static block and initialization block ? 

### A Closer Look at Parameters: Variable Number of Parameters
- A method can be declared to accept a varying numbers of parameter values
- Place an ellipse (...) after parameter type
- Can only be the last type
- Method receives values as an array

```java
public void func (int a, int b, float... list) {
	list.lenght() 		//would work as list is an array
}
func (1, 2, 1.2) 		-> list will be [1.2]
func (p1, p2, 1.3, 2.3) 	-> list will be [1.3, 2,3] 
func (p1, p2, 1.3, 3.4, 4.5) 	-> list will be [1.3, 3.4, 4.5]
```  

### A Closer Look at Parameters: Variable Number of Parameters: Summary -
Parameters are immutable (Changes made to passed value are not visible outsude of method)  
Method can be declared to accept varying number of parameter values(values received as an array, Must be last parameter)

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

### Object Class
Object class is base class in java. By default all classes extend this Object class.

```java
Object o = new CargoFlight();
o.add1Package(1.0, 2.5, 3.0); 		//doesnt work as o reference of Object type doesn't know addPackage.

CargoFlight cf = (CargoFlight) o;
cf.add1Package(1.0, 2.5, 3.0) 		//This runs

if (o instance of CargoFlight) {	//First check before casting as it might result in classCastException otherwise
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

Some important methods in class java.lang.Object :

![noImage](./img/table_11-1.png)


### Equality Of Objects
```java
Flight f1 = new Flight(175);
Flight f2 = new Flight(175);
f1 == f2 	- > 	return false(as reference are checked to be equal)
f1.equals(f2) 	- >	return false(as reference are checked to be equal)
```  
Operator == compares reference of the objects.

**What It Means If You Don't Override equals()?**  
Unless you override equals(), two objects are considered equal only if the two references refer to the same object, since the equals() method in class Object uses only the == operator for comparisons.  

But now we want equal() method to behave differently to make a valid equality comparison of two Flight objects. So we override it.
```java
class Flight {
    private int flightNumber;
    private char flightClass;
    
    @Override
    public boolean equals(Object o) {

        if (!(o instanceof Flight)){
		return false;
	}
	
        Flight other = (Flight) o;
        return flightNumber == other.flightNumber && flightClass == other.flightClass;
    }
}

Now, f1.equals(f2) - > returns TRUE
```  

**What happens in the equals() method ?**  
The object being tested comes in polymorphically as type Object. Hence it doesnt have access to fields of Flight as it is Object type. So we will have to typecast it to a Flight object so that it can access fields of Flight.  
	
But before that you need to do an instanceof test on it just to be sure that you could cast the object argument to the correct type, otherwise, you'll get a runtime ClassCastException if the cast fails.  

Compare the attributes we care about (in this case, just flightNumber and flightClass). 

**:eyes: The first thing in equals method we should do is to check if the current object and the Object o in argument have same reference, then no need to do casting and check attributes. We'll see how to do that later.**  

### Member Hiding and Overriding
Member hiding: 

Overriding: If methods of same signature (Method Signature means method name and parameters) are there in parent and derived Classes, then the method of Derived Class overrides method of BaseClass.

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

If a reference type is of the BaseClass then field accessed is of BaseClass because fields of BaseClass hides the fields of derived class. This may be dangerous.:skull:
But a reference of BaseClass references object of a Derived Class then methods used are of derived class because methods are overridden.

**:bulb: So field accessed depends on reference type used whereas method depends on the constructor used i.e the type of object the reference is pointing to.**  


### Special Reference: Super
A base class variable behaved as if it is variable of derived class, reverse can also be done through super.

Special reference : super
Similar to this, super is an implicit reference to the current object
super treats the object as if it is an instance of its base class
Useful for accessing base class members that have been overridden.  

Eg in the above implementation of equals we would like to do the logic if the references are different as if the references are same, there is no need to go for that logic. So we can use the equals method of Base class that does this.

```java
@Override
public boolean equals (Object o ) {
	if (super.equals(o)) return true;
	
	/rest same/
}
```

### NOTE on Method Overriding 
- Methods must have the same method signature (i.e. method name and parameters).

- Method with the same signature cannot exist in the same class even with a different return type. But can exist in parent class relationship (Overriding  --- remember !). However here also the return type must be the same. (otherwise incompatible type error shown by compiler)

- private methods cannot be overridden. As they can be called within the class only.

- Moreover the method in the child class should not specify a lesser (weaker) access to the overriding method. (A protected method in base class cannot be overriden as private method in child class)

- So method can be overridden when methods of same signature and return type and greater access is there in child class.

**Also Why is greater access of overriden function allowed ?**  
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

By default all classes can be extended. As a result, derived classes have the option to use or override (when allowed) the methods.
**Base class can change these default behaviours. It can control whether it is allowed to be extended and how overriding methods work (whether it wants to prevent overriding or require it).** 

**1) Using "final" keyowrd**
- to prevent inheriting a class 

```java
public final class Passenger {}
```
Now you are not allowed to inherit from this class.

- to prevent overriding a method of the class
```java
public class Flight  {
	public final void add1Package() {
	}
}
```
This allows a class to be inherited from but does not allow a particular method to change. No point of marking class as final because if class is final then you can’t override that class anyway.

**2) Using "abstract" keyword**
- to require inheriting and/or overriding

```java
public class Pilot {
    private Flight currFlight;
    public void fly() {
        if (canAccept(f)) {
            currFlight = f;
        } else {
            handleCanAccept();
        }
    }

    private void handleCanAccept() { 
    	...
    }
}
```

**Where is the canAccept() method ?**  
Our requirement is that the Pilot class has method canAccept() but we don’t know yet what that is. We need to leave the implementation of canAccept() to the derived class that inherits from it. So it allows us to use that method in other method (here in fly method).  

To achieve this we define the method as abstract in the base class.  
```java
public abstract boolean canAccept (Flight f);
```

If a method is abstract, then the whole class must be abstract. So Pilot class has to be abstract.  
```java
public abstract class Pilot { ...same as above }
```

So our class looks like:  
```java
public abstract class Pilot {
    private Flight currFlight;
    
    public void fly() {
        if (canAccept(f)) {
            currFlight = f;
        } else {
            handleCanAccept();
        }
    }

    private void handleCanAccept() { 
    	...
    }
    
    public abstract boolean canAccept (Flight f);
}
```

**:bulb: NOTE - An abstract class can have both abstract and non abstract methods. Its very uncommon to have a class as abstract and method not.**  

```java
public class CargoOnlyPilot extends Pilot {
    @Override
    public boolean canAccept(Flight f) {
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

**:key:Key Points**  
- Fields defined in an interface are static and final by default   
- Fields in an abstract class can be defined as static/non-static object fields   

**Why are all fields in an interface are static and final ?**  
Because no object can be created, thus fields must be static. We need to give that value or capability to all classes that implement this interface.  
All methods & fields in the interface are public Why? because the motive of an interface is to provide the user a set of fields and methods. It makes no sense to make fields private or protected.  


### ENUMERATION Types

Enumeration types are useful for defining a type with a finite list of valid values.  
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
    public CrewMember(FlightCrewJob job) {
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
Implement toString method to provide conversion to a string .
StringBuilder class provides an efficient way to manipulate string values.  

Primitive wrapper classes bring class capabilities to primitive values.
Wrapper classes much less efficient than primitive types.  

Final fields prevent a value from being changed once assigned
Non-static final fields must be set during object instance creation. Static final fields act as named constants.  

Enumeration types useful for defining a type with a finite list of values.  


## Exceptions and Error Handling

### Error Handling with Exceptions
Error handling needs to be implicit in application development. The traditional approach of checking error codes / flags is too intrusive.

**Whenever there is some error, an error object is created by JVM and is thrown. Now what should happen, should the program continue to run or should it give programmers a choice, whether to continue running programme or stop the execution. To give programmers a choice java platform provides exceptions.**   

Exceptions provides a non intrusive way to signal errors.

**Any code can throw an exception: your code, code from a package written by someone else such as the packages that come with the Java platform, or the Java runtime environment. Regardless of what throws the exception, it's always thrown using the throw statement.**  


### ERROR vs EXCEPTIONS
Both Errors and Exceptions are the subclasses of java.lang.Throwable class. 

**An Error** “indicates serious problems that a reasonable application should not try to catch.” Errors are the conditions which cannot get recovered by any handling techniques. It surely cause termination of the program abnormally. Errors belong to unchecked type and mostly occur at runtime. For Eg: 
1) Stack overflow error in case of infinite recursion   
2) Out of memory error in case of exhausting the heap space  

If these cases occur, program cannot continue the execution i.e it will have to terminate and hence JVM throws Throwable object of type Error.

**An Exception** “indicates conditions that a reasonable application might want to catch.” Exceptions are the conditions that may occur at runtime or compile time and may cause the termination of program. But they are recoverable using try, catch and throw keywords. 

Exceptions are divided into two categories : checked and unchecked exceptions. 
- Checked exceptions like IOException are exceptions which compiler necessitates to be catched if thrown in code  
- Unchecked exceptions like ArrayIndexOutOfBoundException, ClassCastException , NullPointerException  WILL NOT BE CHECKED BY  THE compiler (even if you throw theses exceptions explicitly). It is mostly caused by a program written by the programmer and can be rectified by changing logic.  

**try/catch/finally provides a structured way to handle exceptions.**  
1) the try block contains the "normal" code to execute  
Block executes to completion unless an exception is thrown  

2) The catch block contains the error handling code  
Block executes only if matching exception is thrown  

3) The finally block contains cleanup code if needed  
Runs in all cases, following try or catch block  

**Error Handling example**  
C:\Numbers.txt;
5
12
6
4
A lot of things may go wrong here. May be the file doesn’t exist, May be some kind of system error occurred. When we try to read from the file, May be there is bad data in the file (there may be "xyz" in place of number)
So that is why we put everything in a try block;

Whenever we open a file we should be closing it, irrespective of the fact that exception occurred or not. So i.e why we close it in a finally block.

```java
BufferReader reader = null;
int total = 0;

try {
    reader = new BufferReader(new FileReader("C:\Numbers.txt"));
    String line = null;
    while ((line = reader.readLine()) != null) {
        total += Integer.valueOf(line);
    }
    System.out.println("Total:" + total);
} catch (Exception e) {
    System.out.println(e.getMessage());
} finally {
    try {
        // it may be that reader is not defined i.e in error occured in File reading itself. So we put null check there.
        if (reader != null) {
            reader.close();
        } catch {
            System.out.println(e.getMessage());
        }
    }
}
```

### Handling Exceptions by Type
For an object to be able to be thrown, it needs to extend class called "Throwable".
Classes which extend throwable
1) Error - it throws JVM related errors. E.g LinkageErrors. These errors are unchecked (i.e compiler does not require them to be handled.)

2) Exception - This includes
a. RuntimeException - Exceptions like NullPointerException, ArrayIndexOutOfBound , ClassCastException. Runtime Exception class extends Exception class. It is made for the use cases where we want to terminate the thread by throwing an exception. So we can make a custom exception extending RuntimeException and if we throw it, the compiler does not require us to catch it because it cannot be checked by the compiler. So At runtime when it will be thrown and thread will terminate.
These are also unchecked exceptions.

b. Other exceptions extending class Exception. These include exceptions like IOException.
Except the exceptions that extend RuntimeException, ALL OTHER EXCEPTIONS extending "Exception" class are checked exceptions i.e compiler wants them to be handled before hand in code.  

Typed Exceptions
Exception can be handled by type.. i.e Each exception type can have a seperate catch block and they are tested in order and first assignable catch is selected.


### How try-catch works?
When a method has try catch block it puts a marker on the call stack. So if an exception occurs the method with a marker is checked on the call stack, control is passed to that method, thus removing all other method calls from the call stack.

So Exceptions propagate down the call stack. (Can cross method boundaries)
Exceptions are part of a method's contract i.e Method is responsible for any checked exceptions that might occur. It has 2 ways to deal with it:  
1) Catch the exception
2) Intimate that the exception might occur by use of "throws" clause.  

For e.g if we are using FileReader(filename) and reader.readline() in our code. They may throw an exception. So we don’t put try catch in our code as those should be handled by FileReader and realine only. So instead we put the "throws" clause. And Since FileReader says it throws "FileNotFound Exception" and Readline throws "IOException".  

FileNotFoundException is also an IOException, so we can just throw IOException.  

IF WE DIDN’T "CATCH" OR DIDN’T PUT THE "throws" on the method, COMPILER WOULD ACTUALLY COMPLAIN. So by putting the "throws" we say its our responsibility in dealing with it.  


```java
try {
    ....
} finally {
    if (reader != null) {
        reader.close();
    }
}
```

Here if everything runs fine in the try block, then finally block runs and closes reader. Even if exception occurs finally block still runs and closes the file and let the exception call up the call stack.  

**The throws clause of an overriding method must be compatible with the throws clause of the overridden method.**  
Ways to change the throws clause in the overriding method (i.e. in derived class):
1) Not providing any throws clause. (i.e we don't throw any exception that is not already defined in base class.)
2) Can throw the same exception as base class.
3) Can throw a derived exception

WHY SO : -1
Checked exceptions are intended for use in situations where a method may expect its caller to be prepared to deal with certain problems that may arise. If callers of BaseFoo.Bar() are not required to deal with a FnordException, then method DerivedFoo.Bar() cannot expect its callers to deal with a FnordException either (since many of its callers will be the same ones that were unprepared to have BaseFoo.Bar() throw it).

### Throwing Exceptions and Custom Exceptions
We can also throw exceptions to signal that error has occurred or we want to add more information about error that has occurred.  
They are thrown using "throw" keyword.  
Must create exception instance before throwing. Be sure to provide meaningful detail.  
Most exception classes provide a constructor that accepts a String message or other details.  
Now there are cases where we make new exception on top of some other exception to add some info. (tying one exception to another exception).  
So when caused by another exception include originating exception.  
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

### Exceptions and Error Handling: Summary
1) Exceptions provide a non-intrusive way to signal errors
2) try/catch/finally provide a structured way to handle exceptions
3) Exceptions are caught by type
- Can have seperate catch statement for differing exception types
- Catch from most specific to least
4) raise exceptions using throw
5) Methods must declare any unhandled checked exceptions using throw
6) Can create custom exception types
Normally inherit from Exception


## Working with Packages

### What Is a Package?
A package is a group of related types.
- It creates a namespace
- Provide an access boundary
- Act as a unit of distribution

Each source file tells the package it is in.
Use package keyword
1) Package declaration must appear before any type declarations
2) Now all types defined in that source file are part of that package. defined in first line.

### Packages Create a Namespace
Package creates a namespace 
- Package name is part of the type name
- Convention creates unique package name. Follows reverse domain name structure.
- Type name is qualified by package name.

```java
package com.pluralsight.travel;
public class Flight {}
```  

Example of a qualified name
```java
com.pluralsight.travel.Flight lax175 = new com.pluralsight.travel.Flight(175);
```

###  Determining a Type's Package
Compiler needs to know each type's package and explicitly qualifying each package name is impractical.  
For this Java offers several alternatives which allow use of types's simple name.  
1) Types in current package don’t need to be qualified.  
2) Types in the java.lang package dont need to be qualified.  
3) Type Imports  
It guides the compiler to map simple names to qualified names. Use import keyword followed by qualified name.  
a. Single type import - Provides mapping for a single type. this is preferred way.  
b. Import on demand. This provides mapping for all types in a package.  

For example, we have follwing classes:
```java
package com.pluralsight.travel;
public class Flight{}
```  
```java
package com.pluralsight.travel ;
public class Passenger{}
```  
```java
package com.xyzcompany.bar;
public class Beer {}
```  
```java
package com.xyzcompany.bar;
public class Wine {}
```  

**Single Type import**  
```java
import com.pluralsight.travel.Flight;
import com.xyzcompany.bar.Beer;
// telling that we are using Flight class as defined in pluralsight.travel.Flight.

Floght lax175 .= new flight (175);
Beer liteBeer = new Beer();
```  

**Import on Demand**  
```java
import com.pluralsight.travel.*;
import com.xyzcompany.bar.*;

Beer lightBeer = new beer(); // works fine.
Passenger jane = new Passenger(); // works fine
```  

**So Why use single import :question:**  
Take a look at the java API, and you'll see many classes and interfaces with the same name in different packages.  
For example:  java.lang.reflect.Array, java.sql.Array  

So, if you import java.lang.reflect.* and java.sql.* you'll have a collision on the Array type, and have to fully qualify them in your code.

Importing specific classes instead will save you this hassle.

To prevent this either we can import one type, and use qualified name for other, or we can use qualified name for both.  
```java
import java.lang.reflect.Array;

class Test{
  public void test() {
    Array a1 ;
    java.sql.Array a2;
  }
}

//OR

class Test{
  public void test() {
    java.lang.reflect.Array a1 ;
    java.sql.Array a2;
  }
}
```  

### Static import Declarations
(https://howtodoinjava.com/java/basics/static-import-declarations-in-java/)  

### Packages Provide Access Boundaries
How can we make a thing private for a package?  
Package can serve as an access boundary which is often referred to as package private.  
This is useful for creating types and features to support functionality provided by the package which are not meant to be used stand alone.  
This access boundary can apply to a type i.e entire type is inaccessible outside of the package OR can apply to members of a Type i.e Specific members of otherwise accessible type are inaccessible outside of the package.  

1) No access modifier - Visible only within its own package (a.k.a package private)| Usable on types | Usable on members  
2) public - Visible everywhere | EveryWhere | Usable on types | Usable on members  
3) private - Visible Only within its own class | Not Usable on types (if not nested class) | Usable on members.  
4) protected - Visible with its own class and subclass | Not Usable on types (if not nested classes) | Usable on Members.  

private and protected cant be used on types(class). So types cant be private and protected unless they are nested class.  

### Packages Act as a Unit of Distribution
Packages provide a predictable software structure which simplifies distribution. Class files organized in hierarchial folders reflecting the package name. Each part of the package name is separate folder.  

For eg
```java
package com.pluralsight.travel;
public class Flight {}
public class Passenger {}  
```  

When we build this we get the folder structure like this having bytecode :-  
com -> pluralsight -> travel -> Flight.class  
Passenger.class  
So to distribute this, we can copy paste this folder structure  

There is another way to distribute package except through folder structure we saw.
It is through ARCHIVE FILES- that is the entire folder structure can be moved to a single file, commonly called as "jar" files which can then be compressed.  
The archive file may also include manifest that provides info about what is going inside of that archive. It basically contains list of name-value pairs. They are commonly used to define startup class.  

**How to make jar files ?**  
We can make jar files through:
- JDK which provides jar command-line utility.
- IDES
- Build automation systems, also known as build managers like gradle maven.


### Working with Packages: Summary
- A package is a group of related types.
- Package declaration must appear in source file before any type declarations.
- Type name qualified by package name
- Use import statements to map simple names to qualified names
- Packages serve as an access boundary
- Types organized hierarchically according to the package name
- Archive files store package hierarchy in a single file



## Creating Abstract Relationships with Interfaces

### Introducing Interfaces & Implementing an Interface
- An interface defines a contract and provides no implementation.  
- Classes implement interfaces. This implies that the class conforms to the contract.  
- Interfaces don't limit other aspects of the class implementation.  

- Interfaces can accept a parameterized type using a concept known as generics.
```java
public interface Comparable < T > {
    int compareTo(T o);
}

public class Flight implements Comparable < Flight > {
    public int compareTo(Flight f) {
        // no typecast required.
        ....implementation
    }
}

public class Passenger implements Comparable < Passenger > {
    public int compareTo(Passenger p) {
        // no tyecast required
        ...implementation
    }
}
```

- Classes are free to implement multiple interfaces.

E.g Lets say we want to iterate on passengers of Flight class.
```java
Flight lax045 = new Flight (45);

for (Person p: lax045) { 
	... 
}
```  

So we need Flight class to give us iterator through which we can iterate on persons.

For this, Flight class need to implement Iterable/<T> interface. And it will implement Iterable/<Person> i.e it is iterable on person class.

This will enable us to do the following (this is basically what is done by the for-each loop above):  
```java
Iterable<Person> laxIterable = lax045;
Iterator<Person> persons = laxIterable.iterator();
while (persons.hasNext()) {
	Person p = persons.next();
	//Body of for loop
}
```  
So we need Flight class to be iterable and as we want iterator object from object of Flight class that iterate on person of flight, Object of flight class should be able to return an iterator object which can return Person object one after other (So should have hasNext and next method.)


### Implementing Multiple Interfaces

```java
public class Flight implements Comparable < Flight >, Iterable < Person > {
    public int compareTo(Flight f) {
        // no typecast required.
        ....implementation
    }
    
    public Iterator < Person > iterator() {
        return new FlightIterator(crew, roster);
    }
}

public class FlightIterator implements Iterator < Person > {
    boolean hasNext() { 
    	...
    }
    public Person next() { 
    	....
    }
}
```

### Declaring an Interface
Declaring an interface is similar to declaring a class. Just use the interface keyword.
- Supports a subset of the features available to classes
	1) Methods - Name, parameters and return types
	2) Implicitly public

- Constants - Typed named values (Implicitly public final static)  

### Extending interfaces
An interface can extend another interface  
- To add capabilities to existing capabilities
- Implementing extended interface implies implementation of base.  

### Creating Abstract Relationships with Interfaces: Summary
- An interface defines a contract
- Provides no implementation
- Can include methods and constants. By default methods and fields are public. Fields are even static and final constants.
- Classes implements interfaces and are able to implement multiple interfaces
- Interfaces are able to extend other interfaces


## Static Members, Nested Types, and Anonymous Classes

### Static Members
- Static members are shared class-wide
- Not associated with an individual instance
- Declared using the static keyword.
- Accessible using the class name  

**static Field - A value not associated with a specific instance, All instance access same value.**   
**static Method - Not tied to a specific instance, CAN ONLY CALL static methods and ACCESS STATIC FIELDS ONLY.**  


### Static Initialization Blocks
- Performs one time initialization and Executed when a class is loaded in memory  
- Statements enclosed in brackets outside of any method or constructor  
- Static blocks precede with static keyword  
- Cannot access instance members, Must handle all checked exceptions  

```java
public class ABC {
	static {
		.....
	}
} 
```   

**NOTE: Static methods cannot call a non static method or even access non-static members of a class.**  
**Non-static methods can call a static method or access static members of a class.**  


### Nested Types
- A Nested type is a type declared within another type.  
- Classes can be declared within classes and interfaces.  
- Interfaces can be declared within classes and interfaces.
- Nested types are members of the enclosing type.
- Private members of the enclosing type are visible to the nested type.
- Nested types support all member access modifiers: public, package private, protected, private

**:key: Key Points On Access Specifiers**  
1) Protected member means that it can be accessed from any subclass, doesn’t matter from which package it is accessed from. But if it is not accessed from a subclass, then it cannot be accessed from outside of package (package-private).  

2) For class and interfaces: Applicable access modifiers are public and package-private   
For class members: All access modifiers are applicable (static/non-static methods, static/non-static fields, nested class, inner class).

**Nested types serve differing purposes**
Structure and scoping - this is the case when there is no certain relationship between instances of nested and enclosing type. Its just that you want to make the type usable in certain scenarios or you wanna structure its naming relative to another class.  

This happens when you have :  
a. Static classes nested within classes.  
b. All classes nested within interfaces.  
c. all nested interfaces.  

Example: Let's say there is a concept of rewards that is based on memberLevel and memberDays. Often times we have this scenario where two values represent a single concept. So we can wrap that up in a class. 

**We can create rewardsProgramme Class but this is rewardsProgramme as it applies to Passenger. There may be a rewardsProgramme for Crew etc. How to solve this?**  
We can make two separate independent classes, one called PassengerRewardsProgramme and other CrewRewardProgramme.   
				OR 
We can have a rewardsProgramme class that we can nest inside of passenger.   


```java
public static Passenger implements Comparable {
    public static class RewardPrograme {
        private int memberLevel;
        private it memberDays;
        // getters and setters
    }
    
    private RewardPrograme rewardProgram = new RewardProgram();
    
    public RewardProgram getRewardPrograme { 
    	...
    }
}
```

So here is the case of using nested class as a mechanism to provide structure and scoping. Here rewardProgramme is nested static class, hence its name is scoped within the passenger class.

```java
Passenger steve = new Passenger ();
steve.setName("Steve");
steve.getRewardProgram().setLevel(3);
steve.getRewardProgram().setMemberDays(180);

Passenger.RewardProgram platinum = new Passenger.RewardProgram();
platinum.setLevel(3);

if (steve.getRewardProgram().getLevel() == platinum.getLevel()) print("Steve is platinum");
```   
Here we can make a name of a class to be structured inside of another.

**Another Example for static nested class where you require a structure or a naming relative to another class:** We have gridObject for both CatalogGrid and SearchGrid but they may have different attributes in gridObject.  

Now we will see the case if nested class is not marked static.   


### Inner Classes

Each instance of nested class is associated with an instance of the enclosing class. FlightIterator makes no sense unless we have a Flight object i.e Flight Iterator is of some Flight object.  
Non static classes nested within classes

**Example: Remember the code we made for Flight Iterable class and FlightIterator class. We had to pass data of Flight instance as input to constructor of FlightIterator class, so that it can implement hasNext() and next().**  

But with inner class we can create FlightIterator class (marked private and not marked static i.e inner class) inside of Flight class. So that FlightIterator instance is implicitly tied to instance of Flight class and we don’t have to keep duplicates of same data in two different classes.  

And this is more intuitive as FlightIterator class itself gives Iterator. i.e we can ask for Iterator of an iterable by that Iterable class only.

```java
public class Flight implements Comparable < Flight >, Iterable < Person > {
    private CrewMember[] crew;
    private Passenger[] roster;
    
    public Iterator < Person > iterator() {
        return new FlightIterator();
    }

    public FlightIterator iterator() {
        return new FlightIterator();
    }
    
    private class FlightIterator implements Iterator < Person > {
        private int index = 0;
        public boolean hasnext() {
            return index < (crew.length + roster.length);
        }

        public Person next() {
            Person p = (index < crew.length) ? crew[index] : roster[index - crew.length];
            index++;
            return p;
        }
	//IMPORTANT NOTE:  Inner class has "this" referene as it is able to reference index (in index++) 
	//but it was also able to get crew in ( in crew[index] : roster[index - crew,length]); 
	//i.e it also has Flight.this which it used to access members of instance of class in which it was created
    }
}
```

### Anonymous Classes

- Anonymous classes are declared as part of their creation of their object
- Anonymous class is a class jiska object ek hi jagah se banna ho
- Useful for simple interface implementations or class extensions
- Anonymous classes are inner classes and are associated with the enclosing class instance.  
(anonymous class is always inner class because it can’t be used anywhere else except where it is defined. So anonymous class would be used inside of a function which in turn is inside of some class............why?......so that definition can be used to get an instance (of that anonymous class) which is associated directly with the enclosing class inside which instance of anonymous class is used.)
- Create anonymous class as if you are constructing an instance of their interface or base class  
- Place opening and closing brackets after the interface or base class and place implementation code within the brackets
- Implicitly final  
(Agar ek he jagah se object banna hai to main uski definition vohi kyu na du)  

**For Example:** In our Flight class FlightIterator Inner class is used nowhere except the iterator method. That is a great chance to use anonymous class.  

Thus we modify the iterator method like this :  
```java
public Iterator < Person > iterator() {
    return new Iterator < Person > () {
        private int index = 0;
        public boolean hasNext() {
            return index < (crew.length + roster.length);
        }
        public Person next() { ...same implementation
        }
        // Now as this class is inner class it has access to the member of enclosing class.
    };
}
```

**So instead of declaring classes and giving them class names that we are only using at one place, we declare and create the class where we need it.**  

### Static Members, Nested Types, and Anonymous Classes: Summary
1) Static methods and fields are shared class wide (Not associated with individual instance)  
2) Static initialization block provide one time type initialization  
3) A nested type is a type declared within another type and can be used to provide structure and scoping  
4) Inner classes create an association between nested and enclosing instances  
5) Anonymous classes are declared as part of their creation and used as  class extensions  


When reading this again, make required notes from the two links below:
https://beginnersbook.com/2013/05/inner-class/
https://stackoverflow.com/questions/758570/is-it-possible-to-make-anonymous-inner-classes-in-java-static









