---
Owner: Sharafat Karim
Last edited time: 2024-01-27T19:59
---
# Java

Java is a **programming language** and a **platform**. Java is a high level, robust, object-oriented and secure programming language.

# **Platform**

Any hardware or software environment in which a program runs, is known as a platform. Since Java has a runtime environment (JRE) and API, it is called a platform.

# Object-oriented programming

(OOPs) is a methodology that simplifies software development and maintenance by providing some rules.

# JVM (Java Virtual Machine) Architecture

JVM (Java Virtual Machine) is an abstract machine. It is a  
specification that provides runtime environment in which java bytecode  
can be executed.  

The JVM performs following operation:

- Loads code
- Verifies code
- Executes code
- Provides runtime environment

# Classloader

Classloader is a subsystem of JVM which is used to load class files. Whenever we run the java program, it is loaded first by the classloader.

# **Just-In-Time(JIT) compiler**

It is used to improve the  
performance. JIT compiles parts of the byte code that have similar  
functionality at the same time, and hence reduces the amount of time  
needed for compilation. Here, the term "compiler" refers to a translator  
from the instruction set of a Java virtual machine (JVM) to the  
instruction set of a specific CPU.  

# Java Native Interface

Java Native Interface (JNI) is a framework which provides an  
interface to communicate with another application written in another  
language like C, C++, Assembly etc. Java uses JNI framework to send  
output to the Console or interact with OS libraries.  

# Types of Variables

There are three types of variables in [Java](https://www.javatpoint.com/java-tutorial):

- local variable
- instance variable
- static variable

![[/Untitled 15.png|Untitled 15.png]]

i

## Object

[![](https://static.javatpoint.com/images/objects.png)](https://static.javatpoint.com/images/objects.png)

Any entity that has state and behavior is known as an object. For  
example, a chair, pen, table, keyboard, bike, etc. It can be physical or  
logical.  

An Object can be defined as an instance of a class. An object  
contains an address and takes up some space in memory. Objects can  
communicate without knowing the details of each other's data or code.  
The only necessary thing is the type of message accepted and the type of  
response returned by the objects.  

**Example:** A dog is an object because it has states  
like color, name, breed, etc. as well as behaviors like wagging the  
tail, barking, eating, etc.  

## Class

_Collection of objects_ is called class. It is a logical entity.

A class can also be defined as a blueprint from which you can create an individual object. Class doesn't consume any space.

### Inheritance

_When one object acquires all the properties and behaviors of a parent object_, it is known as inheritance. It provides code reusability. It is used to achieve runtime polymorphism.

[![](https://static.javatpoint.com/images/polymorphism.gif)](https://static.javatpoint.com/images/polymorphism.gif)

### Polymorphism

If _one task is performed in different ways_, it is known as  
polymorphism. For example: to convince the customer differently, to draw  
something, for example, shape, triangle, rectangle, etc.  

In Java, we use method overloading and method overriding to achieve polymorphism.

Another example can be to speak something; for example, a cat speaks meow, dog barks woof, etc.

### Abstraction

_Hiding internal details and showing functionality_ is known as abstraction. For example phone call, we don't know the internal processing.

In Java, we use abstract class and interface to achieve abstraction.

[![](https://static.javatpoint.com/images/capsule.png)](https://static.javatpoint.com/images/capsule.png)

### Encapsulation

_Binding (or wrapping) code and data together into a single unit are known as encapsulation_. For example, a capsule, it is wrapped with different medicines.

A java class is the example of encapsulation. Java bean is the fully  
encapsulated class because all the data members are private here.  

### Coupling

Coupling refers to the knowledge or information or dependency of  
another class. It arises when classes are aware of each other. If a  
class has the details information of another class, there is strong  
coupling. In Java, we use private, protected, and public modifiers to  
display the visibility level of a class, method, and field. You can use  
interfaces for the weaker coupling because there is no concrete  
implementation.  

### Cohesion

Cohesion refers to the level of a component which performs a single  
well-defined task. A single well-defined task is done by a highly  
cohesive method. The weakly cohesive method will split the task into  
separate parts. The java.io package is a highly cohesive package because  
it has I/O related classes and interface. However, the java.util  
package is a weakly cohesive package because it has unrelated classes  
and interfaces.  

### Association

Association represents the relationship between the objects. Here,  
one object can be associated with one object or many objects. There can  
be four types of association between the objects:  

- One to One
- One to Many
- Many to One, and
- Many to Many

Let's understand the relationship with real-time examples. For  
example, One country can have one prime minister (one to one), and a  
prime minister can have many ministers (one to many). Also, many MP's  
can have one prime minister (many to one), and many ministers can have  
many departments (many to many).  

Association can be undirectional or bidirectional.

### Aggregation

Aggregation is a way to achieve Association. Aggregation represents  
the relationship where one object contains other objects as a part of  
its state. It represents the weak relationship between objects. It is  
also termed as a  
_has-a_ relationship in Java. Like, inheritance represents the _is-a_ relationship. It is another way to reuse objects.

### Composition

The composition is also a way to achieve Association. The composition  
represents the relationship where one object contains other objects as a  
part of its state. There is a strong relationship between the  
containing object and the dependent object. It is the state where  
containing objects do not have an independent existence. If you delete  
the parent object, all the child objects will be deleted automatically.  

---

## Advantage of OOPs over Procedure-oriented programming language

1) OOPs makes development and maintenance easier, whereas, in a  
procedure-oriented programming language, it is not easy to manage if  
code grows as project size increases.  

2) OOPs provides data hiding, whereas, in a procedure-oriented programming language, global data can be accessed from anywhere.

[![](https://static.javatpoint.com/images/globaldata2.png)](https://static.javatpoint.com/images/globaldata2.png)

Figure: Data Representation in Procedure-Oriented Programming

[![](https://static.javatpoint.com/images/objectdata2.png)](https://static.javatpoint.com/images/objectdata2.png)

Figure: Data Representation in Object-Oriented Programming

3) OOPs provides the ability to simulate real-world event much more  
effectively. We can provide the solution of real word problem if we are  
using the Object-Oriented Programming language.  

---

# Constructors in Java

In [Java](https://www.javatpoint.com/java-tutorial), a constructor is a block of codes similar to the method. It is called when an instance of the [class](https://www.javatpoint.com/object-and-class-in-java) is created. At the time of calling constructor, memory for the object is allocated in the memory.

# **Multithreading**

- **in** [**Java**](https://www.javatpoint.com/java-tutorial) is a process of executing multiple threads simultaneously.

# Thread

A thread is a lightweight subprocess, the smallest unit of processing. It is a separate path of execution.

# Exception Handling in Java

1. [Exception Handling](https://www.javatpoint.com/exception-handling-in-java#)  
2.  
[Advantage of Exception Handling](https://www.javatpoint.com/exception-handling-in-java#exceptionad)  
3.  
[Hierarchy of Exception classes](https://www.javatpoint.com/exception-handling-in-java#exceptionhierarchy)  
4.  
[Types of Exception](https://www.javatpoint.com/exception-handling-in-java#exceptiontypes)  
5.  
[Exception Example](https://www.javatpoint.com/exception-handling-in-java#exceptionexample)  
6.  
[Scenarios where an exception may occur](https://www.javatpoint.com/exception-handling-in-java#exceptionscenarios)

The **Exception Handling in Java** is one of the powerful _mechanism to handle the runtime errors_ so that the normal flow of the application can be maintained.