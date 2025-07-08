# 🔶 Design Patterns

**Design patterns** are typical solutions to common problems in software design. Each pattern is like a _blueprint_ that you can customize to solve a particular design problem in your code.

## 🔷 Groups of design patterns by purpose

- **Creational patterns** concern the process of object creation.
- **Structural patterns** deal with the composition of classes or objects.
- **Behavioral patterns** characterize the ways in which classes or objects interact and distribute responsibility.

The second criterion is **scope**, specifies whether the pattern applies primarily to classes or objects. 
![alt text](images/image.png)

Class patterns deal with relationships between classes and their subclasses, established through inheritance so they are fixed at compile time.
Object patterns deal with relationships, which can be changed at runtime.

![alt text](images/image-1.png)

## 🏗 Creational patterns 

1. **Factory Method**
2. **Abstract Factory**
3. **Builder**
4. **Prototype** 
5. **Singleton**

### 🏭 Factory Method

**Factory method** is a creational design pattern that provides an interface for creating objects in a supperclass, but allows subclasses to alter the type of objects that will be created. The main intent of this pattern is to create objects without exposing the creation logic.

> The Factory Method pattern suggests that you replace direct object construction calls (using the `new` operator) with calls to a special factory method. Objects returned by a factory method are often referred to as `products`.

![alt text](images/image-2.png)

The intent of this design pattern is to create objects, but hiding how this objects are created. It is useful when you have a certain logic that is repeated during the creation of that shared type and when you are duplicating the code for that lets create a method for that. So, the factory method is useful when the class has complex initialisation requirements. 

### 🗯 Abstract Factory

**Abstract Factory** is a creational design pattern that lets you produce families of related objects without specifying their concrete classes.

> The first thing the Abstract Factory pattern suggests is to explicitly declare interfaces for each distinct product of the product family. The next move is to declare the Abstract Factory—an interface with a list of creation methods for all products that are part of the product family.

![abstract-factory](images/image-3.png)

Abstract Factory ensures that products created by a factory are consistent with each other (e.g., ModernChair and ModernTable belong to the same "Modern" family). This is particularly useful when the objects are meant to be used together. It does also promotes loose coupling and encapsulates the creation of objects.

Use the Abstract Factory when your code needs to work with various families of related products, but you don’t want it to depend on the concrete classes of those products—they might be unknown beforehand or you simply want to allow for future extensibility.

### 🔶 Singleton 

**Singleton** is a creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.

❓ How to implement it

- Make the default constructor private, to prevent other objects from using the `new` operator with the Singleton class.
- Create a static creation method that acts as a constructor. Under the hood, this method calls the private constructor to create an object and saves it in a static field. All following calls to this method return the cached object.

> 💡 Use the Singleton pattern when a class in your program should have just a single instance available to all clients.

### 🏗 Builder 

**Builder** is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code.

> 💡 This pattern is particularly useful when an object has many optional or mandatory parameters and different configurations are required during its creation.

![alt text](images/image-4.png)

Instead of creating an object directly using its constructor, you use a Builder class. When you’re done configuring the object, you call a  Build() method of the Builder class, which returns the constructed object.

Use cases :
1. The most common use case for the Builder pattern is when you want to use a mutable object during the initialization phase of an object but want the constructed object to be immutable.
2. A way to abstract the process of building objects.


### 🤖 Prototype

**Prototype** is a creational design pattern that lets you copy existing objects without making your code dependent on their classes.

The Prototype pattern delegates the cloning process to the actual objects that are being cloned. The pattern declares a common interface for all objects that support cloning. This interface lets you clone an object without coupling your code to the class of that object. Usually, such an interface contains just a single `clone` method.

The implementation of the clone method is very similar in all classes. The method creates an object of the current class and carries over all of the field values of the old object into the new one. You can even copy private fields because most programming languages let objects access private fields of other objects that belong to the same class.
![prototype](images/image-5.png)

> 💡 Use the Prototype pattern when your code shouldn’t depend on the concrete classes of objects that you need to copy. 
> ⚡ This happens a lot when your code works with objects passed to you from 3rd-party code via some interface. The concrete classes of these objects are unknown, and you couldn’t depend on them even if you wanted to.
> 🔸 The Prototype pattern provides the client code with a general interface for working with all objects that support cloning. This interface makes the client code independent from the concrete classes of objects that it clones.
---

##  Solid Principles

**_SOLID_** is a mnemonic for five design principles intended to make software designs more **understandable**, **flexible** and **maintainable**.

### 🔴 Single Responsibility Principle

**A class should have just one reason to change.**

> Try to make the class responsible for a part of the functionality provided by the software. if a class does too many things, you have to change it every time one of these things changes. While doing that, you’re risking breaking other parts of the class which you didn’t even intend to change. It suggests that you should a separate class foreach functionality.

### 🟠 Open/Closed Principle

**Classes should be open for extensions but closed not for modifications.**

The main idea of this principle is to keep existing code from breaking when you implement new features. So adding code with changing the existing code.

A class is open if you can extend it, produce a subclass. Also a class is closed when its interface is clearly defined and won't change in the future.

> For example, if a class is already developed, tested, reviewed and included in some framework, or used in the app, trying to mess with its code is risky. Instead of changing directly you can create a subclass and override the parts of the base class that you want to behave differently. 

### 🟡 Liskov Substitution Principle

**When extending a class, you should be able to pass objects of the subclass in place of objects of the parent class without breaking the client code.**

> The substitution principle is a set of checks that help predict whether a subclass remains compatible with the code that was able to work with objects of the super class. 

### 🟢 Interface Segregation Principle

**Clients shouldn’t be forced to depend on methods they do not use.**

> You shouldn't create "fat" interfaces, but more specific ones. Clients should implement only those methods that they really need. 

### 🔵 Dependency Inversion Principle

**High-level classes shouldn't depend on low-level classes. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.**

- **Low-level classes** implement basic operations, such as connecting to database, reading a file.
- **High-level classes** contain complex business logic that direcrs low-level classes to do something.

Usually you solve this using interfaces and implementing dependency injection.
    


