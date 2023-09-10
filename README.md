# Introduction

When creating software, we can follow good practices to avoid issues to make our code easier to understand, robust, and maintainable. Few of these practices are often termed as principles, e.g., the SOLID principles refer to the best practices to be followed in OOD.

SOLID is an acronym for the first five object-oriented design (OOD) principles by Robert C. Martin, also known as Uncle Bob, the author of Clean Code: A Handbook of Agile Software Craftsmanship.

The illustration below represents the acronym for SOLID design principles.

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/SOLID.png">
</p>

# Why use SOLID principles?

Let’s look at the possible issues below that may occur in the code if we don’t adhere to the SOLID principles.

- The code may become tightly coupled with several components, which makes it difficult to integrate new features or bug fixes and sometimes leads to unidentified problems.

- The code will be untestable, which effectively means that every change will need end-to-end testing.

- The code may have a lot of duplication.

- Fixing one issue results in additional errors.

However, if we adhere to the SOLID principles, we are able to do the following:

- Reduce the tight coupling of the code, which reduces errors.

- Reduce the code’s complexity for future use.

- Produce more extensible, maintainable, and understandable software code.

- Produce the code that is modular, feature specific, and is extremely testable.

# Design principles

Let’s look at the definition of the five design principles.

- In the **[Single Responsibility Principle (SRP)](#SPR)**, each class should be responsible for a single part or functionality of the system.

- In the **[Open Closed principle (OCP)](#OCP)**, software components should be open for extension but closed for modification.

- In the **[Liskov Substitution Principle (LSP)](#LSP)**, objects of a superclass should be replaceable with objects of its subclasses without breaking the system.

- The **[Interface Segregation Principle (ISP)](#ISP)** makes fine-grained interfaces that are client specific.

- The **[Dependency Inversion Principle (DIP)](#DIP)**, ensures that the high-level modules are not dependent on low-level modules. In other words, one should depend upon abstraction and not concretion.

## Single Responsability Principle (SRP) <a name="SRP"></a>

The **Single Responsibility Principle (SRP)** is perhaps the least understood of the SOLID concepts. The term was coined by Robert C. Martin who defines the SRP in the following way, "_A class should have only one reason to change._" This implies that any class or component in our code should only have one functionality. Everything in the class should be related to just one goal.

When programmers need to add features or new behavior, they frequently integrate everything within the current class. When something needs to be changed later, due to the complexity of the code, the update process becomes extremely time consuming and tedious. The Single Responsibility Principle helps us create simple classes that perform just one task. This helps in making modifications or adding extensions to the existing code much easier.

### Real-life example

The following illustration represents how SRP is applied in real life:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/SRP.png">
</p>

**Book invoice application**

Let’s try to understand SRP with the help of an example. We have a book invoice application that has two classes: `Book` and `Invoice`. The `Book` class contains the data members related to the book. Whereas, the `Invoice` class contains the following three functionalities:

- Calculating the price of the book

- Printing the invoice

- Saving the invoice into the database

The following class diagram provides a blueprint of these classes:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/without_SRP.png">
</p>

**Violations**
If we notice, the `Invoice` class violates the SRP in multiple ways:

- The `Invoice` class is about invoices, but we have added print and storage functionality inside it. This breaks the SRP rule, which states, "A class should have only one reason to change."

- If we want to change the logic of the printing or storage functionality in the future, we would need to change the class.

Instead of modifying the `Invoice` class for these uses, we can create two new classes for printing and persistence logic: `InvoicePrinter` and `InvoiceStorage`, and move the methods accordingly, as shown below.

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/after_SPR.png">
</p>

### Conclusion

When a class performs one task, it contains a small number of methods and member variables that are self-explanatory. SRP achieves this goal, and due to this, our classes are more usable, and they provide easier maintenance.

## Open-Closed Principle (OCP) <a name="OCP"></a>

In 1988, Bertrand Meyer defined the Open Closed `Principle (OCP)` in the following way, “A software artifact should be open for extension but closed for modification.” This means that a system should improve easily by adding new code instead of changing the code core. This way, the core code always retains its unique identity, making it reusable.

One might think of OCP as inheritance, but remember that inheritance is only one of the OCP techniques. We use the interface because it is open for extension and closed for modification. Therefore, OCP is also defined as `polymorphic OCP`.

### Example

Suppose Alex had a cardboard business that sold boxes to its clients. We designed a class for calculating the volume of boxes. It takes the dimensions and calculates the volume of each box and adds it up to calculate the total volume of all boxes, as shown below.

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/OCP_1.png">
</p>

The volume calculator class

The algorithm for the `volume(Cuboid)` function is shown in the flowchart below.

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/OCP_2.png">
</p>

As the business grew, Alex also started selling cone-shaped boxes. To integrate the calculation of its volume, we need to make a `Cone` class and update the` volume()` function. See the updated classes below:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/OCP_3.png">
</p>
The algorithm for the `volume(Shape)` function is shown in the flowchart below.

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/OCP_4.png">
</p>

With only two types of boxes, the class structure looks fine, but what if Alex decides to deal with more types of boxes, e.g., a cylinder box? This will add complexity to the `volume(Shape)`. We will divide the code into segments using OCP to overcome this complexity.

### Implementing the Open Closed Principle

We will make a parent class, `Shape`, which is an abstract class and has a `volume()` function, that is extended by its sub-classes, `Cuboid`, `Cylinder`, and `Cone`. These derived classes have their own `volume()` functions according to the shape. Then we have the `VolumeCalculator` class that only performs one task: adding the volume of all the boxes using the `sumVolume()` function.

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/OCP_5.png">
</p>

### Conclusion

We can conclude the OCP discussion as follows:

- A software system should be easy to extend without the need for modification in the existing system. For the software systems, this goal is achieved by OCP.

- The system must be divided into small components, which are arranged, so that core code is always protected from new code.

## Liskov Substitution Principle (LSP) <a name="LSP"></a>

The **Liskov Substitution Principle (LSP)** is one of the fundamental design principles of object-oriented design. The LSP helps guide the use of inheritance in design so that the application does not break. It states that the objects of a subclass should behave the same way as the objects of the superclass, such that they are replaceable. This rule generally applies to abstraction concepts like inheritance and polymorphism.

### The Vehicle class

Let's construct a simple class called `Vehicle` that has some attributes and methods and a subclass `Car` that extends it as shown below:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/LSP_1.png">
</p>

So far, this implementation seems right since a car IS A vehicle, and the `startEngine()` method will override the superclass method. However, it's not as simple as it looks.

### Violation

Let's add a `Bicycle` subclass in this system and see what happens:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/LSP_2.png">
</p>

This results in a problem. A bicycle is a vehicle, but it does not have an engine. Therefore, the `Bicycle` class should not be allowed to override the `startEngine()` method.

### Solution

A possible fix to this issue would be to add two subclasses of `Vehicle` that classify the vehicles as motorized vehicles and manual vehicles as follows:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/LSP_3.png">
</p>

With this implementation, we have satisfied the LSP.

- `Car` is substitutable with its superclass, `Motorized`, and `Bicycle` is substitutable with its superclass, `Manual`, without breaking the functionality.

- Their methods can also override the methods of the superclass.

### Conclusion

The LSP is an important principle that should be extended to the level of system architecture. A small violation of the substitutability of classes can cause the system to break down, which is why we should always be on the lookout for violations. A few benefits of the LSP are provided below:

- It avoids the generalization of concepts that may not be needed in the future.

- It makes the code maintainable and easier to upgrade.

## Interface Segregation Principle (ISP) <a name="ISP"></a>

The **Interface Segregation Principle (ISP)** is a design principle that does not recommend having methods that an interface would not use and require. Therefore, it goes against having fat interfaces in classes and prefers having small interfaces with a group of methods, each serving a particular purpose.

The goal behind implementing the ISP is to have a precise code design that follows the correct abstraction guidelines and tends to be more flexible, which would help in making it more robust and reusable. This becomes key when more and more features are added to the software, making it bloated and harder to maintain.

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/ISP_1.png">
</p>

### Example

Let’s construct a simple interface called `Shape` that has the `area()` method, and `Square` and `Rectangle` as the classes to implement it as shown below:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/ISP_2.png">
</p>

So far, this implementation seems right as both the `Square` and `Rectangle` classes are implementing an interface that they’re using. Let’s see how the ISP can be violated by this example.

### Violation

Let’s add the `volume()` method to the `Shape` interface and have a new subclass `Cube` to implement it:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/ISP_3.png">
</p>

The violation leads to a problem. The 2-D shapes cannot have a volume, yet they’re forced to implement the `volume()` method of the `Shape` interface that they don’t have any use of. This is a clear violation of the Interface Segregation Principle.

### Solution

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/ISP_4.png">
</p>

Now, there are two interfaces present: `Shape` and `Shape3D`. The `Shape` interface contains only the methods that are required for 2-D shapes like squares, rectangles, etc., while the `Shape3D` interface inherits the methods of the `Shape` interface and itself only contains methods for 3-D shapes like cubes, spheres, etc.

Since each class is now implementing an interface that they need to use, the Interface Segregation Principle is now no longer being violated.

### Conclusion

The ISP, being an important principle, is the most violated principle in object-oriented programming. This can easily be achieved by adding more features to our software, requiring us to update large parts of our program. A few benefits of the ISP are as follows:

- It helps to keep our software maintainable and robust.

- It allows for efficient refactoring and redeployment of code.

## Dependency Inversion Principle (DIP) <a name="DIP"></a>

The **Dependency Inversion Principle (DIP)** states that high-level modules should not depend on low-level modules, but rather both should depend on abstractions. The abstractions should not depend on details. Instead, the details should depend on abstractions.

In many cases, thinking about the interaction between modules as an abstract concept allows the linking of components to be reduced without the need for more coding patterns to be implemented. This allows for a functional scheme with reduced implementation and allows the system to be more flexible.

### Real-life example

Let’s try to understand the concept of DIP with the help of a school example. Suppose there is a headmaster of a high school. Under the headmaster, there are faculty members such as teachers, assistants, and some helpers.

#### Violation

Let’s see what a possible design would look like without the implementation of the DIP.

The class diagram of this example is shown below:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/DIP_1.png">
</p>

Let’s note down some issues with this design:

- Everything is exposed from the lower layer to the upper layer, meaning that abstraction has not been implemented. This indicates that the headmaster must know the type of faculty that they can oversee beforehand.

- Now, if an additional type of faculty comes under the headmaster, such as a secretary, then the entire system would need to be reconfigured.

### Solution

A possible fix to this issue would be to add a `Faculty` class that will be the parent class for all types of faculty. This would reduce the number of dependencies among modules and would make for an easily expandable system.

Let’s look at the DIP implemented in class diagram below:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/DIP_2.png">
</p>

Now, if any other kind of faculty is employed, they can just be easily added to the `Headmaster` without the need to explicitly inform the headmaster of it. Let’s take the example of an additional faculty position, `Secretary`. Its class would be a child of the `Faculty` class and would lead to the following diagram:

<p align="center">
<img src="https://github.com/tutungduong/solid_guide/blob/main/images/DIP_3.png">
</p>

With this implementation, we have decoupled some of the modules, and therefore, satisfied the Dependency Inversion Principle.

### Conclusion

The DIP reduces the number of dependencies among modules. It provides a layer of abstraction between lower and higher classes, allowing for changes in the lower class without making changes in the higher class. A few benefits of the DIP are as follows:

- It allows for the flexibility and stability of the software.

- It allows for the reusability of the application modules.
