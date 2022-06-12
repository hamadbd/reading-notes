## What is an Object in Python?
Python is a programming language that focuses on object-oriented programming. In Python, almost everything is an object. We can check if the python is an object using the type(). It is just a collection of variables and Python functions. There are various types of objects in Python such as Lists, dictionaries, files, sets, strings and etc. An object is defined by its class. For example, an integer variable is a member of the integer class. An object is a physical entity. The properties of an object are as follows. State, Identity, and behavior are the three key properties of the object.
Concept of Python Class
The definition of Python class is simply a logical entity that behaves as a prototype or a template to create objects. Python classes provide methods that could be used to modify an object’s state. They also specify the qualities that an object may possess.

## Python Class Variables
All object instances of a class share a Python class variable. When a class is being created, variables are defined. They aren’t defined in any of a class’ methods.

Variables and functions are defined inside the class and are accessed using objects. These variables and functions are collectively known as attributes.

## Example of Python Classes and Objects
Let’s take an example to understand the concept of Python classes and objects. We can think of an object as a regular day-to-day object, say, a car. Now as discussed above, we know that a class has the data and functions defined inside of it, and all this data and functions can be considered as features and actions of the object, respectively. That is, the features (data) of the car (object) are color, price, number of doors, etc. The actions (functions) of the car (object) are speed, application of brakes, etc. Multiple objects with different data and functions associated with them can be created using a class

## Advantages of Using Classes in Python
- Classes provide an easy way of keeping the data members and methods together in one place which helps in keeping the -program more organized.
- Using classes also provides another functionality of this object-oriented programming paradigm, that is, inheritance.
- Classes also help in overriding any standard operator.
- Using classes provides the ability to reuse the code which makes the program more efficient.
- Grouping related functions and keeping them in one place (inside a class) provides a clean structure to the code which - increases the readability of the program.

## Types of Classes in Python
There are various types of classes in Python in which some are as follows:

- Python Abstract class
- Python Concrete class
- Python Partial Class
- Let’s get into detail to under

## Python Abstract Class
An abstract class is a class that contains one or more abstract methods. The term “abstract method” refers to a method that has a declaration but no implementation. When working with a large codebase, it might be difficult to remember all classes. That is when a Python Abstract class can be used. Python, unlike most high-level languages, does not have an abstract class by default.

A class can be defined as an abstract class using abc.ABC, and a method can be defined as an abstract method using abc.abstractmethod. The abbreviation for abstract base class is ABC. The ABC module, which provides the foundation for building Abstract Base classes, must be imported. The ABC module operates by decorating base class methods as abstract. It installs concrete classes as the abstract base’s implementations.

Example:
```
From abc import ABC, abstractmethod
Class AbstractClassName(ABC):
@abstract method
def abstract_method_name(self):
Pass
```

## The_init_() Function in Python
In python classes, “__init__” method is reserved. It is automatically called when you create an object using a class and is used to initialize the variables of the class. It is equivalent to a constructor.

Like any other method, init method starts with the keyword “def”
“self” is the first parameter in this method just like any other method although in case of init, “self” refers to a newly created object unlike other methods where it refers to the current object or instance associated with that particular method.
Additional parameters can be added
Following example illustrates how to use the __init__() function:
```
class IntellipaatClass:
    def __init__(self, course):
        self.course = course
    def display(self):
        print(self.course)
object1 = IntellipaatClass("Python")
object1.display()
Output:
Python
```
In the above example, the init function behaves as a constructor and is called automatically as soon as the ‘object1 = IntellipaatClass(“Python”)’ statement is executed. Since it is a function inside a class, the first argument passed in it is the object itself which is caught in the ‘self’ parameter. The second parameter, i.e., course, is used to catch the second argument passed through the object, that is ‘Python’. And then, we have initialized the variable course inside the init function. Further, we have defined another function named ‘display’ to print the value of the variable. This function is called using object1.