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
- Main file - Main.java
- Folder in which compiled classes will go - folder1/folder2/classes
- Location of Helper.java  
> folder1/folder2/project/src/com/mantiso/Helper.java and it is used as “com.mantiso.Helper” in Main.java.
- then command would be (and we run command from inside of folder 1).. then command would be  
    javac -d folder2/classes -sourcepath folder2/project/src ../Main.java

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

javac command understands package in terms of source folder. First of all it starts compiling the file mentioned in the file you are mentioning as your main file (lets say mentionedMainFile). So if import com.PackageName.ClassName is there in main file then javac checks from directory relative to sourcepath  and checks whether a file with name com.PackageName.ClassName exists or not.  

For this it sees whether package named “com.PackageName” exists or not .. if not it gives error that com.PackageName does not exist . for it to exist there should be folder structure com/PackageName after source folder.  If this happens then there should a file called ClassName.java inside of it inside of which package mentioned should also be “com.PackageName” as each java file tells its name using its packageDeclaration. If in file com/PackageName/ClassName ,,, package name mentioned is com.AnotherPackageName then it is saying that my name is com.AnotherPackageName.ClassName…. Not com.PackageName.ClassName .. So javac would say …. Bad source file com/PackageName.ClassName .. bad because file does not contain “com.PackageName.ClassName” class (as it contains  com.AnotherPackageName.ClassName)   

com.Pluralsight.SomeClass.java in source folder goes in  …. coom/PluralSight/SomeClass.class in class folder  

## WHAT HAPPENS AFTER CLASS IS COMPILED.. WE RUN THE APPLICATION

When running the application I.e we run a command “java” to run the application …. we need CLASSPATH. … i.e to run machine code java needs the location where all the .class files are located so that it can load those files in the machine. That location is the CLASSPATH.

- we can set CLASSPATH globally by set CLASSPATH="path of folder containing .class files i.e ‘classes’ in our case" and run java command which needs two things 1) CLASSPATH and 2) the name of the Main class which has main function here com.pluralsight.Main.
- If CLASSPATH is not given then it takes the classpath from environment variable i.e the CLASSPATH which is set globally.
- The command we run is java com.pluralsight.Main
- But setting global path would affect every application on the system. So better is to provide classpath while running java  .. 
            java -cp $pathToClasses $packageName.ClassName

- So e.g
  java -cp classes com.pluralsight.Main
  we can also provide multiple classpaths separating them by ":"
  java -cp $pathToClasses1:$pathToClasses2 $packageName.ClassName

What does multiple class path mean?  
It is just that java will load classes from these class paths. Lets say i use a class named “com.packageName.ClassName”. This package may be in $pathToClasses1 or $pathToClasses2 so if java does not find packageName in $pathToClasses1 it goes to $pathToClasses2 to find this class to load it in JVM.

So lets make a jar file and put some class in it and move it somewhere else.

So let us say we create jar file for Helper.java by using command 
jar cvf helper.jar src/com/mantiso/Helper.class
This will create Helper.jar in currentDirectory (which is like a folder containing com/mantiso/Helper.class This structure inside jar file is made using package declaration inside Helper.class)

lets move it somewhere else to ../lib
and now delete Helper.class
del classes/com/mantiso/Helper.class

So there is no Helper class in com/mantiso .. where is it then ….. In the jar file. So if we run 
java -cp classes com.pluralsight.Main   
This would return error as it will not find com.mantiso.Helper

So we give another folder in classpath
java -cp classes:lib/Helper.jar com.pluralsight.Main
and code runs

Why … as class named com.mantiso.Helper.class is in Helper.jar which is kinda folder. Which contains com/mantiso/Helper.class .



So we have seen that java class are compiled using javac command (using a MainFile MentionedMain.java) and compiled into a folder… and run using java command using a Main .class file and classPath where java would find classes needed for our code (which are compiled earlier using javac command).



So Now what else we will study ..

ClassLoading basics
Writing our own classloader
Using classloading delegation
Hot deploying Java code
Understanding Java reflection
Using reflection to implement a simple IOC container

