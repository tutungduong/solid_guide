# Introduction

When creating software, we can follow good practices to avoid issues to make our code easier to understand, robust, and maintainable. Few of these practices are often termed as principles, e.g., the SOLID principles refer to the best practices to be followed in OOD.

SOLID is an acronym for the first five object-oriented design (OOD) principles by Robert C. Martin, also known as Uncle Bob, the author of Clean Code: A Handbook of Agile Software Craftsmanship.

The illustration below represents the acronym for SOLID design principles.

## Hình Solid title The SOLID design principle in object-oriented design

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

- In the **Single Responsibility Principle (SRP)**, each class should be responsible for a single part or functionality of the system.

- In the **Open Closed principle (OCP)**, software components should be open for extension but closed for modification.

- In the **Liskov Substitution Principle (LSP)**, objects of a superclass should be replaceable with objects of its subclasses without breaking the system.

- The **Interface Segregation Principle (ISP)** makes fine-grained interfaces that are client specific.

- The **Dependency Inversion Principle (DIP)**, ensures that the high-level modules are not dependent on low-level modules. In other words, one should depend upon abstraction and not concretion.

<!-- Explanation about the SOLID principles

<p align="center">
<img height="570" width="1572" alt="Image1" src="https://user-images.githubusercontent.com/13514156/120488978-df9e8100-c37c-11eb-80ec-e1fc38f0f19d.jpeg">
</p>

**SOLID** is an acronym that represents five principles very important when we develop with the **OOP** paradigm, in addition it is an essential knowledge that every developer must know.
Understanding and applying these principles will allow you to write better quality code and the therefore be a better develop

The SOLID principles were defined in the early 2000s by Robert C Martin (Uncle Bob). Uncle Bob elaborated some of these and identified others already existing and said that these principles should be used to get a good management of dependencies in our code

However, in the begining these principle were not yet known as SOLID until Michael Feathers observed that the initials of these principles fit perfectly under the acronym SOLID and that it was also a very representative name for iths definition

These principles help us to obtain the following benefits:

- Ease to maintain
- Ease to extend
- Robust code

But before we see what each SOLID principle means, we need to remember two relevant concepts in the development of any software, The **COUPLING** and the **COHESION**

`COUPLING:`
We can define it as the degree to wich a class, method or any other software entity, is directly linked to another. This degree of coupling can also be seen as a degree of dependence.

`COHESION:`
Is the measuare in which two or more partes of a sustem work together to obtain better results than each part individually -->

<!-- ## The SOLID principles

<p align="center">
<img height="470" width="1472" alt="Image1" src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*d1h-XOnl7IWIyddvITcCKg.png">
</p>

- **S** - Single Responsability Principle
- **O** - Open Closed Principle
- **L** - Lisko Substitucion Principle
- **I** - Interface Segregation Principle
- **D** - Dependency Inversion Principle -->

## Single Responsability Principle (SRP)

<!-- A class should have a single function.

A class should be responsible for only one thing. The moment it acquires more responsibility it becomes docked, something that is not desirable if you want to ensure the maintenance of the application. This is because changing one of your responsibilities may affect the other and vice versa. -->

The **Single Responsibility Principle (SRP)** is perhaps the least understood of the SOLID concepts. The term was coined by Robert C. Martin who defines the SRP in the following way, "_A class should have only one reason to change._" This implies that any class or component in our code should only have one functionality. Everything in the class should be related to just one goal.

When programmers need to add features or new behavior, they frequently integrate everything within the current class. When something needs to be changed later, due to the complexity of the code, the update process becomes extremely time consuming and tedious. The Single Responsibility Principle helps us create simple classes that perform just one task. This helps in making modifications or adding extensions to the existing code much easier.

### Real-life example

The following illustration represents how SRP is applied in real life:

**An exmaple of SRP ( hinh + title)**

**Book invoice application**

Let’s try to understand SRP with the help of an example. We have a book invoice application that has two classes: `Book` and `Invoice`. The `Book` class contains the data members related to the book. Whereas, the `Invoice` class contains the following three functionalities:

- Calculating the price of the book

- Printing the invoice

- Saving the invoice into the database

The following class diagram provides a blueprint of these classes:

**The class diagram of the book invoice application without applying the SRP rule**

**Violations**
If we notice, the `Invoice` class violates the SRP in multiple ways:

- The `Invoice` class is about invoices, but we have added print and storage functionality inside it. This breaks the SRP rule, which states, "A class should have only one reason to change."

- If we want to change the logic of the printing or storage functionality in the future, we would need to change the class.

Instead of modifying the `Invoice` class for these uses, we can create two new classes for printing and persistence logic: `InvoicePrinter` and `InvoiceStorage`, and move the methods accordingly, as shown below.

**Hinh` The class diagram of the book invoice application after applying the SRP rule**

### Conclusion

When a class performs one task, it contains a small number of methods and member variables that are self-explanatory. SRP achieves this goal, and due to this, our classes are more usable, and they provide easier maintenance.

<!-- ```java

class Vehicle {

    String brand;

    Vehicle(String brand){
        this.brand = brand;
    }

     String getVehicleIdentifier() {
        return brand;
     }

     void saveVehicle(Vehicle vehicle) {
        //Implementation for save into database...
      }
}
```

This class violates SRP. Why? The single responsibility principle states that each class should have a single function. However, the class **Vehicle** handles both properties ( getVehicleIdentifier) and database storage ( saveVehicle). This means that if, for example, a change occurs in the storage system of our application, it is likely to affect the way in which the properties are managed, forcing us to change the class Vehicleas well as the classes that are using it.

In other words, the SRP establishes a high degree of stiffness , so that there is no domino effect every time a change occurs.

One way to solve the previous example would be the following:

```java

class Vehicle {
    String brand;

    Vehicle(String brand){
        this.brand = brand;
    }
    String getVehicleIdentifier() {
        return brand
    }
}

class VehicleDB {
    saveVehicle(Vehicle vehicle) {
        //Implementation for save into database
    }
    getVehicle(int idVehicle) {
        return idVehicle;
     }
}
``` -->

## Open-Closed Principle (OCP)

In 1988, Bertrand Meyer defined the Open Closed `Principle (OCP)` in the following way, “A software artifact should be open for extension but closed for modification.” This means that a system should improve easily by adding new code instead of changing the code core. This way, the core code always retains its unique identity, making it reusable.

One might think of OCP as inheritance, but remember that inheritance is only one of the OCP techniques. We use the interface because it is open for extension and closed for modification. Therefore, OCP is also defined as `polymorphic OCP`.

### Example

Suppose Alex had a cardboard business that sold boxes to its clients. We designed a class for calculating the volume of boxes. It takes the dimensions and calculates the volume of each box and adds it up to calculate the total volume of all boxes, as shown below.

OCP_1

The volume calculator class

The algorithm for the `volume(Cuboid)` function is shown in the flowchart below.

OCP_2 The volume(Cuboid) function

As the business grew, Alex also started selling cone-shaped boxes. To integrate the calculation of its volume, we need to make a `Cone` class and update the` volume()` function. See the updated classes below:

OCP_3 The volume(Cuboid) function

The algorithm for the `volume(Shape)` function is shown in the flowchart below.

OCP_4 The volume(Cuboid) function

With only two types of boxes, the class structure looks fine, but what if Alex decides to deal with more types of boxes, e.g., a cylinder box? This will add complexity to the `volume(Shape)`. We will divide the code into segments using OCP to overcome this complexity.

### Implementing the Open Closed Principle

We will make a parent class, `Shape`, which is an abstract class and has a `volume()` function, that is extended by its sub-classes, `Cuboid`, `Cylinder`, and `Cone`. These derived classes have their own `volume()` functions according to the shape. Then we have the `VolumeCalculator` class that only performs one task: adding the volume of all the boxes using the `sumVolume()` function.

OCP_5 The class diagram of VolumeCalculator according to OCP

### Conclusion

We can conclude the OCP discussion as follows:

- A software system should be easy to extend without the need for modification in the existing system. For the software systems, this goal is achieved by OCP.

- The system must be divided into small components, which are arranged, so that core code is always protected from new code.

<!-- It establishes that the software entities (classes, modules and functions) should be open for their extension, but closed for their modification.

Let's continue with our class **Vehicle**:

If we wanted to iterate through a list of vehicles and print their marks on the screen:

```java
class Vehicle {
    String brand;

    Vehicle(String brand){ this.brand = brand; }

    String getBrandVehicle(){ return brand; }
}
```

If we wanted to iterate through a list of vehicle and print their brands on the screen:

```java
public static void main(String[] args) {
    Vehicle[] arrayVehicles = {
            new Vehicle("Ford"),
            new Vehicle("Audi")
    };
    printAveragePriceVehicle(arrayVehicles);
}

public static void printAveragePriceVehicle(Vehicle[] arrayVehicles){
    for (Vehicle vehicle : arrayVehicles) {
        if(vehicle.brand.equals("Ford")) System.out.println(18000);
        if(vehicle.brand.equals("Audi")) System.out.println(25000);
    }
}
```

This would not fulfill the open / closed principle, since if we decide to add a new vehicle from another brand:

```java
Vehicle[] arrayVehicles = {
    new Vehicle("Ford"),
    new Vehicle("Audi"),
    new Vehicle("Mercedes")
};
```

We would also have to modify the method that we created previously:

```java
public static void printAveragePriceVehicle(Vehicle[] arrayVehicle){
    for (Vehicle vehicle : arrayVehicle) {
        if(vehicle.brand.equals("Ford")) System.out.println(18000);
        if(vehicle.brand.equals("Audi")) System.out.println(25000);
        if(vehicle.brand.equals("Mercedes")) System.out.println(27000);
    }
}
```

As we can see, for each new car new logic would have to be added to the printAveragePriceVehicle () method. This is a simple example, but imagine that your application grows and grows… how many modifications would we have to make? Better to avoid this waste of time and headache, right?

To comply with this principle we could do the following:

```java
abstract class Vehicle {
    // ...
    abstract int averagePriceVehicle();
}

class Ford extends Vehicle {
    @Override
    int averagePriceVehicle() { return 18000; }
}

class Audi extends Vehicle {
    @Override
    int averagePriceVehicle() { return 25000; }
}

class Mercedes extends Vehicle {
    @Override
    int averagePriceVehicle() { return 27000; }
}

public static void main(String[] args) {

    Vehicle[] arrayVehicles = {
            new Ford(),
            new Audi(),
            new Mercedes()
    };

    printAveragePriceVehicle(arrayVehicles);
}

public static void printAveragePriceVehicle(Vehicle[] arrayVehicles){
    for (Vehicle vehicle : arrayVehicles) {
        System.out.println(vehicle.averagePriceVehicle());
    }
}
```

Each vehicle extends the abstract class **Vehicle** and implements the abstract method averagePriceVehicle().

Thus, each vehicle has its own implementation of the averagePriceVehicle () method, so the printAveragePriceVehicle () method iterates through the array of vehicles and only calls the averagePriceVehicle() method.

Now, if we add a new vehicle, averagePriceVehicle () will not have to be modified. We will only have to add the new vehicle to the array, thus fulfilling the open / closed principle. -->

## Liskov Substitution Principle (LSP)

The **Liskov Substitution Principle (LSP)** is one of the fundamental design principles of object-oriented design. The LSP helps guide the use of inheritance in design so that the application does not break. It states that the objects of a subclass should behave the same way as the objects of the superclass, such that they are replaceable. This rule generally applies to abstraction concepts like inheritance and polymorphism.

### The Vehicle class

Let's construct a simple class called `Vehicle` that has some attributes and methods and a subclass `Car` that extends it as shown below:

LSP_1 The vehicle superclass

So far, this implementation seems right since a car IS A vehicle, and the `startEngine()` method will override the superclass method. However, it's not as simple as it looks.

### Violation

Let's add a `Bicycle` subclass in this system and see what happens:

LSP_2 The vehicle superclass

This results in a problem. A bicycle is a vehicle, but it does not have an engine. Therefore, the `Bicycle` class should not be allowed to override the `startEngine()` method.

### Solution

A possible fix to this issue would be to add two subclasses of `Vehicle` that classify the vehicles as motorized vehicles and manual vehicles as follows:

LSP_3 An example of the LSP implementation

With this implementation, we have satisfied the LSP.

- `Car` is substitutable with its superclass, `Motorized`, and `Bicycle` is substitutable with its superclass, `Manual`, without breaking the functionality.

- Their methods can also override the methods of the superclass.

### Conclusion

The LSP is an important principle that should be extended to the level of system architecture. A small violation of the substitutability of classes can cause the system to break down, which is why we should always be on the lookout for violations. A few benefits of the LSP are provided below:

- It avoids the generalization of concepts that may not be needed in the future.

- It makes the code maintainable and easier to upgrade.

<!-- It declares that a subclass must be substitutable for its superclass, and if by doing this the program crashes, we are violating this principle.

Fulfilling this principle, it will be confirmed that our program has an easy to understand class hierarchy and reusable code.

Let's see an example:

```java
// ...
public static void printnNumbersSeats(Vehicle[] arrayVehicles){
    for (Vehicle vehicle : arrayVeicles) {
        if(vehicle instanceof Ford)
            System.out.println(numSeatsFord(vehicle));
        if(vehicle instanceof Audi)
            System.out.println(numSeatsAudi(vehicle));
        if(vehicle instanceof Mercedes)
            System.out.println(numSeatsMercedes(vehicle));
    }
}
printNumSeats(arrayVehicles);
```

This violates both the Liskov substitution principle and the open / closed principle. The program must know each type of vEHICLE and call its associated numSeats () method.

Thus, if we add a new Vvehicle, the method must be modified to accept it.

```java
// ...
Vehicle[] arrayVehicles = {
        new Ford(),
        new Audi(),
        new Mercedes(),
        new Ferrari()
};

public static void printnNumbersSeats(Coche[] arrayVehicles){
    for (Vehicle vehicle : arrayVehicles) {
        if(vehicle instanceof Ford)
            System.out.println(numASeatsFord(vehicle));
        if(vehicle instanceof Audi)
            System.out.println(numSeatsAudi(vehicle));
        if(vehicle instanceof Mercedes)
            System.out.println(numSeatssMercedes(vehicle));
        if(vehicle instanceof Ferrari)
            System.out.println(numSeatsFerrari(vehicle));
    }
}
printnNumbersSeats(arrayVehicles);
```

For this method to comply with the principle, we will follow these principles:

If the superclass (Vehicle) has a method that accepts a parameter of the type of the superclass (Vehicle), then its subclass (Ford) should accept as an argument a type of the superclass (Vehicle) or a type of the subclass (Ford).
If the superclass returns a type of itself (Vehicle), then its subclass (Ford) should return a type of the superclass (Vehicle) or a type of the subclass (Ford).
If we implement the previous method again:

```java
public static void printnNumbersSeats(Vehicle[] arrayVehicles){
        for (Vehicle vehicle : arrayvehicles) {
            System.out.println(vehicle.numSeats());
        }
    }

printnNumbersSeats(arrayVehicles);
```

Now the method doesn't care about the class's type, it just calls the superclass's numSeats () method. It only knows that the parameter is of type vehicle, either Vehicle or one of the subclasses.

For this, now the Vehicle class must define the new method:

```java
abstract class Vehicle {

    // ...
    abstract int numSeats();
}
```

And the subclasses must implement such a method:

```java
class Ford extends Vehicle {

    // ...
    @Override
    int numSeats() {
        return 5;
    }
}
// ...
```

As we can see, now the printnNumbersSeats () method does not need to know what type of car it is going to perform its logic with, it simply calls the method numSeats () of the Vehicle type, since by contract, a subclass of Vehicle must implement said method. -->

## Interface Segregation Principle (ISP)

The **Interface Segregation Principle (ISP)** is a design principle that does not recommend having methods that an interface would not use and require. Therefore, it goes against having fat interfaces in classes and prefers having small interfaces with a group of methods, each serving a particular purpose.

The goal behind implementing the ISP is to have a precise code design that follows the correct abstraction guidelines and tends to be more flexible, which would help in making it more robust and reusable. This becomes key when more and more features are added to the software, making it bloated and harder to maintain.

ISP_1 Having small interfaces for more robust software

### Example

Let’s construct a simple interface called `Shape` that has the `area()` method, and `Square` and `Rectangle` as the classes to implement it as shown below:

ISP_2 The Shape interface

So far, this implementation seems right as both the `Square` and `Rectangle` classes are implementing an interface that they’re using. Let’s see how the ISP can be violated by this example.

### Violation

Let’s add the `volume()` method to the `Shape` interface and have a new subclass `Cube` to implement it:

ISP_3 The Shape interface

The violation leads to a problem. The 2-D shapes cannot have a volume, yet they’re forced to implement the `volume()` method of the `Shape` interface that they don’t have any use of. This is a clear violation of the Interface Segregation Principle.

### Solution

ISP_4 The Shape interface

Now, there are two interfaces present: `Shape` and `Shape3D`. The `Shape` interface contains only the methods that are required for 2-D shapes like squares, rectangles, etc., while the `Shape3D` interface inherits the methods of the `Shape` interface and itself only contains methods for 3-D shapes like cubes, spheres, etc.

Since each class is now implementing an interface that they need to use, the Interface Segregation Principle is now no longer being violated.

### Conclusion

The ISP, being an important principle, is the most violated principle in object-oriented programming. This can easily be achieved by adding more features to our software, requiring us to update large parts of our program. A few benefits of the ISP are as follows:

- It helps to keep our software maintainable and robust.

- It allows for efficient refactoring and redeployment of code.

<!-- This principle states that clients should not be forced to rely on interfaces they do not use.

In other words, when a client depends on a class that implements an interface whose functionality this client does not use, but which other clients do use, this client will be affected by the changes that other clients force on that interface.

Let's imagine that we want to define the necessary classes to house some types of birds. For example, we would have parrots, toucans, and hawks:

```java
interface IBird {
    void fly();
    void eat();
}

class Parrot implements IBird{

    @Override
    public void fly() {
        //...
    }

    @Override
    public void eat() {
        //..
    }
}

class Hawk implements IBird{
    @Override
    public void fly() {
        //...
    }

    @Override
    public void eat() {
        //..
    }
}
```

So far so good. But now let's imagine we want to add the penguins. These are birds, but they also have the ability to swim. We could do this:

```java
interface IBird {
    void fly();
    void eat();
    void swim();
}

class Parrot implements IBird{

    @Override
    public void fly() {
        //...
    }

    @Override
    public void eat() {
        //...
    }

    @Override
    public void swim() {
        //...
    }
}

class Penguin implements IBird{

    @Override
    public void fly() {
        //...
    }

    @Override
    public void comer() {
        //...
    }

    @Override
    public void eat() {
        //...
    }
}
```

The problem is that the parrot does not swim, and the penguin does not fly, so we would have to add an exception or warning if we try to call these methods. Furthermore, if we wanted to add another method to the IAve interface, we would have to go through each of the classes that implements it and add the implementation of that method to all of them. This violates the principle of interface segregation, since these classes (the clients) do not have to depend on methods they do not use.

The best thing to do would be to segregate the interfaces further, as necessary. In this case we could do the following:

```java
interface IBird {
    void eat();
}
interface IFlyingBird {
    void fly();
}

interface ISwimmingBird {
    void swim();
}

class Parrot implements IBird, IFlyingBird{

    @Override
    public void fly() {
        //...
    }

    @Override
    public void eat() {
        //...
    }
}

class Penguin implements IBird, ISwimmingBird{

    @Override
    public void swim() {
        //...
    }

    @Override
    public void eat() {
        //...
    }
}
```

Thus, each class implements the interfaces of which it really needs to implement its methods. When adding new functionalities, this will save us a lot of time, and in addition, we comply with the first principle (Single Responsibility). -->

## Dependency Inversion Principle (DIP)

The **Dependency Inversion Principle (DIP)** states that high-level modules should not depend on low-level modules, but rather both should depend on abstractions. The abstractions should not depend on details. Instead, the details should depend on abstractions.

In many cases, thinking about the interaction between modules as an abstract concept allows the linking of components to be reduced without the need for more coding patterns to be implemented. This allows for a functional scheme with reduced implementation and allows the system to be more flexible.

### Real-life example

Let’s try to understand the concept of DIP with the help of a school example. Suppose there is a headmaster of a high school. Under the headmaster, there are faculty members such as teachers, assistants, and some helpers.

#### Violation

Let’s see what a possible design would look like without the implementation of the DIP.

The class diagram of this example is shown below:

DIP_1 Violation of the DIP

Let’s note down some issues with this design:

- Everything is exposed from the lower layer to the upper layer, meaning that abstraction has not been implemented. This indicates that the headmaster must know the type of faculty that they can oversee beforehand.

- Now, if an additional type of faculty comes under the headmaster, such as a secretary, then the entire system would need to be reconfigured.

### Solution

A possible fix to this issue would be to add a `Faculty` class that will be the parent class for all types of faculty. This would reduce the number of dependencies among modules and would make for an easily expandable system.

Let’s look at the DIP implemented in class diagram below:

DIP_2 DIP example of a high school

Now, if any other kind of faculty is employed, they can just be easily added to the `Headmaster` without the need to explicitly inform the headmaster of it. Let’s take the example of an additional faculty position, `Secretary`. Its class would be a child of the `Faculty` class and would lead to the following diagram:

DIP_3 DIP example of a high school

With this implementation, we have decoupled some of the modules, and therefore, satisfied the Dependency Inversion Principle.

### Conclusion

The DIP reduces the number of dependencies among modules. It provides a layer of abstraction between lower and higher classes, allowing for changes in the lower class without making changes in the higher class. A few benefits of the DIP are as follows:

- It allows for the flexibility and stability of the software.

- It allows for the reusability of the application modules.

<!-- It states that the dependencies must be in the abstractions, not in the concretions. That is to say:

- High-level modules should not rely on low-level modules. Both should depend on abstractions.
- Abstractions shouldn't depend on details. Details should depend on abstractions.
  At some point our program or application will become made up of many modules. When this happens, it is when we must use dependency injection, which will allow us to control the functionalities from a specific place instead of having them spread throughout the program. Furthermore, this isolation will allow us to perform testing much more easily.

Suppose we have a class to access data, and we do it through a DB:

```java
class DatabaseService{
    //...
    void getData(){ //... }
}

class AccessData {

    private DatabaseService databaseService;

    public AccessData(DatabaseService databaseService){
        this.databaseService = databaseService;
    }

    Dato getData(){
        databaseService.getDatos();
        //...
    }
}
```

Let's imagine that in the future we want to change the DB service for a service that connects to an API. For a minute to think what should be done ... Do you see the problem? We would have to modify all the instances of the AccesoADatos class, one by one.

This is because our high-level module (AccesoADatos) depends on a lower-level module (DatabaseService), thus violating the principle of dependency inversion. The high-level module should depend on abstractions.

To fix this, we can make the DataAccess module depend on a more generic abstraction

```java
interface Connection {
    Data getData();
    void setData();
}

class AccessData {

    private Connection conectionn;

    public AccessData(Connection connection){
        this.connection = connection;
    }

    Data getData(){
        connection.getData();
    }
}
```

Thus, regardless of the type of connection that is passed to the AccessData module, neither it nor its instances will have to change, so we will save a lot of work.

Now, each service that we want to pass to AccessData must implement the Connection interface:

```java
class DatabaseService implements connection {

    @Override
    public Data getData() { //... }

    @Override
    public void setData) { //... }
}

class APIService implements Connection{

    @Override
    public Data getData() { //... }

    @Override
    public void setData() { //... }
}
```

Thus, both the high-level and low-level modules depend on abstractions, so we comply with the principle of inversion of dependencies. Furthermore, this will force us to comply with the Liskov principle, since the types derived from Connection (DatabaseService and APIService) are substitutable by their abstraction (Connection interface). -->
