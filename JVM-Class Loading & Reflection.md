# Understanding the Java Virtual Machine: Class Loading and Reflection

Practically speaking, a runtime environment is a piece of software that is designed to run other software. As the runtime environment for Java, the JRE contains the Java class libraries, the Java class loader, and the Java Virtual Machine. In this system:
- The class loader is responsible for correctly loading classes and connecting them with the core Java class libraries.
- The JVM is responsible for ensuring Java applications have the resources they need to run and perform well in your device or cloud environment.
- The JRE is mainly a container for those other components, and is responsible for orchestrating their activities. So JRE is like an OS for Java machine called JVM. (loading programs, memory management, synchronization, scheduling)

 The JRE is the on-disk system that takes your Java code, combines it with the necessary libraries, and starts the JVM to execute it.

![noImage](./img/table_11-1.png)


Java code compiles to .class files (having byte code which JVM understands). These classes (i.e .class files) have to be loaded into virtual machine.  

**Where does Java load its .class files from ?**  
It should be able to locate them. So it uses something called classpath.  

**What is the classpath ?**  
This is a collection of locations maybe on the file system, maybe on the network, maybe in a database, where classes (.class files) are held and Java runtime can load classes from anywhere on this classpath. 

These are various ways of setting classpath. 
  - Globally (not a good idea).
  - Locally when we run the Java application (better).


## WHAT HAPPENS BEFORE COMPILATION
Above is the scene after the files are compiled at a location. But what is the scene when file is not compiled i.e it is in the form of “.java“.

- The package name inside of a java class determines the folder structure at the location where compiled files(.class files) will go.  (Name of a class is package.NameOFClass)
- Compiler starts compiling code starting from a file mentioned as Main file. Lets call it Main.java
- Lets say we have Main.java defined in the package “com.pluralsight” and uses class named “com.mantiso.Helper” inside of a folder src/com/mantiso/Helper.java Main.java can be anywhere
- So we run a command to compile Main.java and put compiled classes in a folder called “classes” which can be anywhere

**javac -d $pathToClassesFolder -sourcepath $pathToSourceFolder $pathToMain.java**  

Lets say we have 
- Main file 
> Main.java

- Folder in which compiled classes will go 
> folder1/folder2/classes

- Location of Helper.java that will be imported as “com.mantiso.Helper” in Main.java
> folder1/folder2/project/src/com/mantiso/Helper.java 

- Run compile command from inside of folder 1  
> javac -d folder2/classes -sourcepath folder2/project/src ../Main.java

```
└───Main.java  
│
└───folder1  
│   └───folder2 
│   |   └───project  
│   |   |   └───src  
│   |   |       └───com
│   |   |           └───mantiso  
│   |   |               └───Helper.java 
│   |   |
|   |   └───classes 
```

javac command understands package in terms of source folder. 
First of all it starts compiling the Main file mentioned in the command. Here it is Main.java  

**Level I Verification:**  
If import com.PackageName.ClassName is there in main file then javac starts checking from directory relative to sourcepath and checks whether a file with name com.PackageName.ClassName exists or not.  

For this it first checks whether package named “com.PackageName” exists or not. (**NOTE:** for it to exist there should be folder structure com/PackageName after the source folder)  
If the folder structure does not exist then it gives error that com.PackageName does not exist . 

If it exists then there should be a file called ClassName.java.

**Level II Verification:** 
Inside of the file ClassName.java, the package mentioned should also be “com.PackageName” as each java file tells its name using its packageDeclaration. 

If the package name mentioned is com.AnotherPackageName then it is saying that my name is com.AnotherPackageName.ClassName…. Not com.PackageName.ClassName .. So javac would say …. Bad source file com/PackageName.ClassName .. bad because file does not contain “com.PackageName.ClassName” class (as it contains com.AnotherPackageName.ClassName)   

com.Pluralsight.SomeClass.java in source folder goes in  …. com/PluralSight/SomeClass.class in class folder  

## WHAT HAPPENS AFTER CLASS IS COMPILED.. WE RUN THE APPLICATION

When running the application i.e we run a command “java” to run the application …. we need CLASSPATH. … i.e to run machine code java needs the location where all the .class files are located so that it can load those files in the machine. That location is the CLASSPATH.

- we can set CLASSPATH globally by set CLASSPATH="path of folder containing .class files i.e ‘classes’ in our case"  
  Run java command which needs two things 1) CLASSPATH and 2) the name of the Main class which has main function here com.pluralsight.Main.
> java -cp classes com.pluralsight.Main
  
- If CLASSPATH is not given then it takes the classpath from environment variable i.e the CLASSPATH which is set globally.
  Run java command which just needs the name of the Main class which has main function here com.pluralsight.Main.
> java com.pluralsight.Main
  
- But setting global path would affect every application on the system. So better is to provide classpath while running java 

            
  java -cp $pathToClasses $packageName.ClassName

  we can also provide multiple classpaths separating them by ":"
  java -cp $pathToClasses1:$pathToClasses2 $packageName.ClassName

What does multiple class path mean?  
It is just that java will load classes from these class paths. Lets say i use a class named “com.packageName.ClassName”. This package may be in $pathToClasses1 or $pathToClasses2 so if java does not find packageName in $pathToClasses1 it goes to $pathToClasses2 to find this class to load it in JVM.

So lets make a jar file and put some class in it and move it somewhere else.

So let us say we create jar file for Helper.java by using command 
jar cvf Helper.jar src/com/mantiso/Helper.class
This will create Helper.jar in currentDirectory (which is like a folder containing com/mantiso/Helper.class **This structure inside jar file is made using package declaration inside Helper.class**)

lets move it somewhere else to ../lib
and now delete Helper.class
del classes/com/mantiso/Helper.class

So there is no Helper class in classes/com/mantiso (.. where is it then ….. In the jar file). So if we run 
java -cp classes com.pluralsight.Main   
This would return error as it will not find com.mantiso.Helper

So we give another folder in classpath
java -cp classes:lib/Helper.jar com.pluralsight.Main
and code runs

Why … as class named com.mantiso.Helper.class is in Helper.jar which is kinda folder. Which contains com/mantiso/Helper.class .


**What did we learn :question:**  
We have seen that java class are compiled using javac command (using a MainFile MentionedMain.java) and compiled into a folder… and run using java command using a Main .class file and classPath where java would find classes needed for our code (which are compiled earlier using javac command).



**What else we will study :question:**  

ClassLoading basics
Writing our own classloader
Using classloading delegation
Hot deploying Java code
Understanding Java reflection
Using reflection to implement a simple IOC container


## CLASSLOADING

**What is classLoading ?**   
- ClassLoading is loading of byte code of class definitions into JVM by classLoaders who know how to load them. 
- Classloaders come with JRE .
- The smallest unit of execution that gets loaded by a ClassLoader is the Java class file. 
- A class file contains the byte code representation of a Java class, which has the executable bytecodes and references to other classes used by that class, including references to classes in the Java API.  

Stated simply, a ClassLoader locates the bytecodes for a Java class that needs to be loaded, reads the bytecodes, and creates an instance of the java.lang.Class type(or class). This makes the class available to the JVM for execution. Initially when a JVM starts up, nothing is loaded into it. The class file of the program being executed is loaded first and then other classes and interfaces are loaded as they get referenced in the bytecode being executed. The JVM thus exhibits lazy loading, i.e., loading classes only when required, so at start-up the JVM doesn't need to know the classes that would get loaded during runtime. Lazy loading plays a key role in providing dynamic extensibility to the Java platform. The Java runtime can be customized in interesting ways by implementing a custom ClassLoader in a program, as I'll discuss later.

So what must be happening is JVM make a Class Object and using that... every instance of that object must be created…. CHECK.

**What will we study ?**
- **Core classes** (default classes like String), How they are loaded. 
- **Extension classes** - classes that oracle want to ship with every class but not part of core classes
 OR
classes shipped by “third party” that we want to be shipped with every Java application
- **Delegation model in java** - when a classloader attempts to load a class it delegate its call to parent classloader which call its parent classloader and so on until root at which point it cascades back till some classloader can load the class.
- **Displaying this delegation**


### Core Java Classes And extension classes
Except from classpath there are two other locations that java loads its classes from.
1) inside the **"jre"** directory we have **rt.jar(runtime.jar)** which has basic files like String.class etc i.e the core classes.
2) in the **"ext"** folder inside "jre" directory , we have jar files having java classes used by many apps but aren’t part of core libraries (i.e rt.jar)

**So jre/rt.jar and jre/ext/somejarFiles.jar are loaded except CLASSPATH**   

Note: So ….  if we move lib/helper.jar to ext folder and remove lib/helper.jar from classpath then code would work fine  

Lets say we run **java -cp classes com.pluralsight.Main**
- While "COMPILING" if we remove com/mantiso.Helper.java then it will say com.mantiso.Helper not found.
BUT  
if we put helper.jar in "ext" (extension) folder then even after removing com/mantiso/Helper.java,  code compiles successfully, using helper.jar in "ext" folder.

There are **two extension directories possibly**, one used by the Java runtime environment  (JRE) and one used by the java JDK (inside jre folder in JDK which also includes src.zip containg sourcecode e.g String.java) and these could be in different places. the appropriate one will be picked up depending upon the version of java you use.

we can also set the extension directory path explicitly.
**java -cp $classpath -D java.ext.dirs=$pathToExtnsionFolder com.pluralsight.Main**

So in all , classloaders have ‘CLASSPATH’ and ‘rt.jar’ and ‘ext’ folder to load  the compiled  class files from. And we can specify extension folder ‘ext’ folder location also explicitly.

**So … where are we till now in the course.**
So we have studied that there are classloaders who load the files in JVM(reads byte code of class files and create java.lang.Class instance). and where from these classloaders find the files to load. Now we will study that there are different types of classloaders and which classloader loads which class.




