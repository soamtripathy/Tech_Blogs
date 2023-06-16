---
title: "Abstraction Vs Encapsulation"
seoTitle: "Abstraction vs Encapsulation in Python: OOP Explained"
seoDescription: "Understand the differences between abstraction and encapsulation in Python's OOP paradigm. Learn with examples and grasp their significance."
datePublished: Fri Jun 16 2023 06:03:13 GMT+0000 (Coordinated Universal Time)
cuid: cliy5yo8e000f09jj81oz49k6
slug: abstraction-vs-encapsulation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686895021162/f735cacb-b4c1-4a32-aaa6-d2268392fe83.jpeg
tags: programming-blogs, python, oops, abstraction, encapsulation

---

### Introduction

Object-Oriented Programming (OOP) is a powerful paradigm that allows developers to organize and structure their code in a more intuitive and efficient manner. Two key concepts in OOP are abstraction and encapsulation, which play vital roles in designing robust and maintainable software systems. In this article, we will explore the concepts of abstraction and encapsulation in Python, highlighting their differences, benefits, and providing examples to demonstrate their practical usage.

**Abstraction: Hiding Complexity**

Abstraction is the process of hiding unnecessary details and exposing only essential features of an object or system. It allows developers to focus on high-level functionality without getting lost in the implementation details. Abstraction is achieved through abstract classes and interfaces in Python.

An abstract class is a blueprint for other classes and cannot be instantiated itself. It defines common attributes and methods that subclasses must implement. By defining an abstract class, we can ensure that subclasses adhere to a certain structure or behaviour.

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @abstractmethod
    def start(self):
        pass
    
    @abstractmethod
    def stop(self):
        pass
    
class Car(Vehicle):
    def start(self):
        print("Car started.")
    
    def stop(self):
        print("Car stopped.")

class Bike(Vehicle):
    def start(self):
        print("Bike started.")
    
    def stop(self):
        print("Bike stopped.")
```

In the example above, the `Vehicle` class is an abstract class with two abstract methods, `start()` and `stop()`. The subclasses `Car` and `Bike` inherit from the `Vehicle` class and provide their own implementations for these methods. The abstract class enforces that any subclass of `Vehicle` must have these methods, ensuring the desired behaviour without specifying the implementation details.

**Encapsulation: Data Protection and Hiding**

Encapsulation is the practice of bundling data and methods together within a class, thereby hiding the internal state and implementation details from the outside world. It provides data protection and ensures that the internal state of an object can only be accessed through well-defined methods, known as getters and setters, or properties in Python.

Let's consider an example of encapsulation:

```python
class BankAccount:
    def __init__(self):
        self._balance = 0
    
    def deposit(self, amount):
        self._balance += amount
    
    def withdraw(self, amount):
        if amount <= self._balance:
            self._balance -= amount
        else:
            print("Insufficient balance.")
    
    def get_balance(self):
        return self._balance
```

In the above example, the `BankAccount` class encapsulates the `_balance` variable and provides methods to interact with it. The `deposit()` and `withdraw()` methods allow users to modify the account balance, while the `get_balance()` method provides read-only access to the balance. By encapsulating the balance and providing controlled access, we ensure that the balance can only be modified through the defined methods, maintaining data integrity.

**Differences between Abstraction and Encapsulation**

While abstraction and encapsulation are closely related concepts, they serve different purposes in object-oriented programming:

1. Abstraction focuses on hiding unnecessary details, emphasizing the essential characteristics of an object or system. It provides a high-level view and simplifies complexity.
    
2. Encapsulation focuses on bundling data and methods within a class, restricting direct access to the internal state of an object. It ensures data protection and enables controlled access to the object's attributes.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686895053332/50f7475b-e131-40e6-9a56-21771f4d7650.png align="center")
    

**Benefits of Abstraction and Encapsulation**

Abstraction and encapsulation offer several benefits that contribute to the overall quality and maintain ability of software systems:

1. Modularity: Both abstraction and encapsulation promote modularity in code. By hiding implementation details and exposing only essential features, modules or classes can be developed independently, leading to more manageable and reusable code.
    
2. Code Reusability: Abstraction allows the creation of abstract classes or interfaces that can be inherited by multiple subclasses. This enables code reuse, as subclasses can inherit and implement the required functionality, reducing redundancy and improving code efficiency.
    
3. Maintainability: Abstraction and encapsulation contribute to the maintainability of code. By hiding implementation details, changes can be made to the internal structure of a class without affecting the code that uses it. This reduces the impact of changes and makes maintenance and updates easier.
    
4. Security and Data Integrity: Encapsulation protects data by allowing controlled access through methods or properties. It ensures that data can only be modified through defined operations, reducing the risk of accidental or unauthorized modifications and maintaining data integrity.
    
5. Flexibility and Extensibility: Abstraction provides a flexible and extensible code structure. The abstract classes or interfaces can be extended to create new subclasses, adding new functionality while maintaining compatibility with existing code. This allows for the easy addition of new features without impacting the existing codebase.
    

**Example Demonstrating Abstraction and Encapsulation**

Let's consider a real-life example to demonstrate the practical usage of abstraction and encapsulation in Python:

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    def __init__(self, name):
        self._name = name
    
    @abstractmethod
    def make_sound(self):
        pass
    
    def get_name(self):
        return self._name
    
class Dog(Animal):
    def make_sound(self):
        print("Woof!")
    
class Cat(Animal):
    def make_sound(self):
        print("Meow!")
    
class Zoo:
    def __init__(self):
        self._animals = []
    
    def add_animal(self, animal):
        self._animals.append(animal)
    
    def show_animals(self):
        for animal in self._animals:
            print(f"{animal.get_name()} says: ", end="")
            animal.make_sound()

# Usage example
zoo = Zoo()
dog = Dog("Buddy")
cat = Cat("Whiskers")

zoo.add_animal(dog)
zoo.add_animal(cat)

zoo.show_animals()
```

In this example, the `Animal` class is an abstract class with an abstract method `make_sound()` and a protected attribute `_name`. The `Dog` and `Cat` classes inherit from the `Animal` class and provide their own implementations of the `make_sound()` method. The `Zoo` class encapsulates a list of animals and provides methods to add animals to the zoo and display the sounds they make.

### Conclusion

Abstraction and encapsulation are fundamental concepts in object-oriented programming that promote code organization, modularity, reusability, and maintainability. Abstraction focuses on hiding unnecessary details and emphasizing essential features, while encapsulation protects data by bundling it with methods within a class. By leveraging these concepts, developers can design software systems that are easier to understand, maintain, and extend. Python provides powerful mechanisms such as abstract classes, interfaces, and access modifiers that enable developers to implement abstraction and encapsulation effectively in their code.