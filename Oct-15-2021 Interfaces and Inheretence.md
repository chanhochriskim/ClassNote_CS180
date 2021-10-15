# Inheritance 
## Problem
- sometimes classes have related or overlapping functionality.
- consider a program for keepign track of personall at the college. 
- Need a Person class to keep information.
- But also might want special classes for 
	- Student: to include grades or classes taken. 

Person Class
``` 
public class Person {
private String name; 
private String address; 

public Person (String name, String address) {
this.name = name;
this.address = address; 
}
public String getName() {return name;}
public String getAddress() {return address;}
public void setAddress(String address) {..continued}
} 

```

Student Classes (refer the lecture slide.)

## Inheritance
- rather than duplicating members among these classes, **JAVA** allows classes to share member definitions in a hierarchical fashion. 
- One class can 'extend' another 'inheriting' fields and methods from it.
- Terminology: the 'subclass' inherits

### Inheritance - example
- class Person has fields name, address, as well as accessors and mutators
- Class student 'extends' Person
	- Inerhits the fields and methods from Person 
	- adds classes and grades (and more accessors and mutators)

- Class Professor 'extends' Person 
	- inherits the fields and methods from Person 
	- Adds rank and salary 

- Common fields and methods go in Person, and are inherited by its subclasses. 

Student Subclass (code - refer the lecture slide.)

## Classes and Subclasses 
- Student s = new Student (...);
- String[] classes = s.getClasses();
- String name = s.getName();
- double gpa = s.getGPA();
- ...
- Student t = s; 
- Student t = s.clone();  

ex:
Perosn fred = new Student(...);
String name = fred.getName();
Account ch = new Checking(...); (it's ok to use superclass variables)

## Object Class 
- One designated class in Java - Object- is the root of all clases 
	- everythnig else is sub-class.

- Any class that doesnt extend another class implicitly extends the Object class.
- A class can only extend one other class ( but can implement multiple interfaces. )
- Java is a 'single inheritance' system.
- C++ is a 'multiple inheritance' system. 


## Subclass Object
- contains its fields as well as all the fields dfeined in its superclasses.


## Object Class Methods 
- The object class has a small number of public methods. Samples >>>
	- clone() - makes a copy of the object
	- equals(Object e) - compares for equality
	- toString() - returns a String representation
- The toString() method is very handy: 
	- It is called by printf and similar methods when a String...

## Constructor Chaining 
- Whenconstructing an object of a class, it is important that all the constructors up the inheritance chain have an opportunity to initilaize the object under construction. 
- Called constructor chaining
- Java enforces constructor chaining by inserting implicit calls to superclass constructors 
- you can override this behavior by inserting your own calls

## Constructor Rules 
- EVERY class must have at least one constructor 
- the FIRST line of every constructor must be a call to another constructor.

## Default Constructors 
- If you don't provide any constructors in a class, Java provides one for you:
```
public ClassName() {
super();
}
```
- the statement 'super();' calls the 0-argument constructor in the superclass

## Default Chaining
- If you DO provide a constructor...
- by default Java interts the statement
- ``` super(); ```
- at the beginning to enforce. 


## Explicit Chaining
- You can explicitly call a superclass constructor yourself 
- Useful for passing arguments 'up the line' to initialize the object using superclass constructors 
- see the Student example earlier
- ...
- The first step in each constructor is to either
	- call another constuctor in the current class, or
	- call a superclass constructor 
- to call another constructor, use this(...) 
- to call a superclass constructor, use super(...)
- you can do one or the other but not BOTH
- In either case, the argument types are matched with the class constructors to find a match.  
- If no explicit this(...) or super(...) is provided in a constructor, Java automatically calls super() (the superclass constructor with no arguments)

## Constructor Complications 
- If the base class does not have a parameterless constructor, the derived class constructor must make an explicit call, with super(...), to an available constructor in the base class.

## super() and this()
- Recall that this can be used to call another constructor in the current class 
- If you call this, Java does not call super
- the consturcotr you call must either call this or super, so super will eventually be called
- If specified explicitly, calls to super or this, must be the first staement in a constructor 

## Wheel example (refer to the lecture slide)

## Terminology 
- Student extends Person 
- Student is a subclass of Person
- Person is a superclass of Student 
- Person is the parent class, Student is the child class
- Person is the base clas, Student is a derived class. 


## Reminder: Java Access Modifiers 
- Can apply to members: fields and methods 
- Modifiers control access to members from methods in other classes 

## Subclass Access 
- subclasses can't access private fields in their superclasses
- Two options:
	- Leave as is; provide accessors and/or mutators 
	- Change private to protected 
- Protected allows subclass access to superclass fields (even if the subclass is in a different package.)
- General Advice: use accessors and mutators 

## Overloading vs Overriding
- Overloading - in the same class, two methods with the same name,  but different signatures 
- Overriding - in a superclass and subclass, two methods with the same name, same signature 

## Overriding Methods 
- A subclass method with the same signiature as a superclass method overrides blah blah blah (refer to the lecture slide)

## Accessing Overridden Methods
 - overriden methods can also be accessed using super: super.method	