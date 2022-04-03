# Java vs Python
    - Java is strongly typed, where as python is weekly typed
    - Python is slower than Java
    - Java is preferred over python for very large scale projects(may be billions of user)

### Python Execution Process
    - Stage1 : Syntax Checking and Translation (Compilation Step)
        - I/P : Python Code 
        - O/P : Byte Code
    - Stage2 : Python Virtual Machine(PVM)
        - I/P : Byte Code
            - Converts byte code to machine code. Executes this machine code and provide output.
        - O/P : output of python code
### print argument
- end : It tells you what do you want at the end ?
    - It is not a separator, rather it tells you what do you want at the end ?
```python
print(10 end= " and ")
print(20)
# It will print "10 and 20"
print(10, 20 end = " and ")
print(30)
# It will print 10 20 and 30
```
- separator : It tells you how to separate the data
```python
print(10, 30, 40, sep=",", end = " and ")
print(20)
# It will print 10, 30, 40 and 20
print("Hello world", "I am Anurag Modi", "I am 30 years old", sep=".")
# Hello World.I am Anurag Modi.I am 30 years old
```
### Weakly typed languages
- javascript, kotlin, python
- typescript :- strongly typed version of javascript. typescript is more used nowadays.
- a strongly typed language is always better than a weekly typed languages
- in weekly typed you do not have to specify the type of the variable.
- in strongly typed you need to specify the type of the variable.

### Get ascii value of a char
```python
x = "b"
print(ord(x))

# map A -> 0
a = ord("a") - ord("a")    # a = 0
a = ord("b") - ord("a")    # b = 1
z = ord("z") - ord("a")    # z = 25
```

### char increment
```python
x = "a"                            # get the 10th char from a
new_char = chr(ord("a") + 10)      # will give 10th char from a
```

# OOPS
#### Encapsulation
- Similar things should be kept together.

#### Classes
- A class is a user defined blueprint or prototype from which objects are created. 
- It represents the set of properties or methods that are common to all objects of one type.

#### Objects:
An object consists of 3 things
- state : It is represented by the attributes of an object. It also reflects the properties of an object
    - Ex. Breed, Age, Color
- Behavior : It is represented by the methods of an object. It also reflects the response of an object to other objects.
    - Ex. Bark, Sleep, Eat
- Identity : It gives a unique name to an object and enables one object to interact with other objects.
    - Ex. Name of Dog (tommy)

#### self keyword
- self represents the current object to which some function/attribute is associated.

#### Constructors
- It is the first thing that is called whenever an object is created. The closest to a constructor in python is "__init__" method.
- constructor is also used for initialization of data members.
- python does not have any destructor. Garbage collection happens automatically. But there is a method in python which gets called in python whenever an object goes out of scope. Its name is `del` method.
- During garbage collection `del` method is called.
```python
class Dog:
    def __init__(self):
        print("I am the closest thing to a constructor")
    def __del__(self):
        print("I am closest thing to a destructor")
```
- Tip : In python we do not have block scopes. 
    - Meaning if an object is created inside an `if` statement, that does not mean it will be deleted, once we come outside of is statement. Python has function based scoping. 
    - Objects only gets deleted once the go out of function scope.
    - del is just a method called by destructor/garbage collector. But it itself is not a destructor. When we call del method ourselves however it does not deletes the object
    - order of deletion is same as order of creation.
#### Polymorphism
- The word polymorphism means having many forms. Ability of sth to exist in multiple forms
- 2 types
    - overloading (add operator)    (type of data decides what kind of operation needed to be done)
        - based on different number/type of arguments
        - print( 2 + 10)
        - print("Anurag" + "Modi")
        - len([1,2,3,4])                   # len is overloaded 
        - len("anuragm")                   # len is overloaded
        - def add(a, b, z=0)               # overloaded function, it supports both 2 and 3 args
        - (on runtime we decide which bark method to invoke)    # 2 classes having same function (ex. can_fly())
    - overrriding
        - It happens using inheritance only
        - When in the derived class, u are overriding the function that is present in the base class

#### Inheritance
Inheritance is the capability of one class to inherit the property of another class . Relationship created in inheritance is `is-a` relationship.

Benefits:
    - Code Reusability
    - Better Code Design
    - Lesser Code Change

Types of Inheritance:
    - Single
    - Multiple
    - Multilevel
        - A - > B -> C (B inheriting from A, C inheriting from B).
        - C will have access to all properties of B as well as A
        - This is an example of indirect inheritance
    - Hierarchical

    - Diamond Problem : Hybrid Inheritance
                SuperClass                # Hierarchical Inheritance
                  /     \
               ClassA  ClassB             # Multiple Inheritance
                  \     /
                   ClassC

#### Abstract Base Classes
- Abstract Classes are always base classes from which other classes inherit