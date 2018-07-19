---
permalink: /cpp/class
layout: single
classes: wide
title:  "Class and Objects"
tags: [C++, notes]
date:   2018-07-19
sidebar:
  nav: "cpp"
---



Object Oriented Programming (OOP) is a programming style that is intended to make thinking about programming closer to thinking about the real world.

In programming, **objects are independent units, and each has its own identity**, just as objects in the real world do.

An apple is an object; so is a mug. Each has its unique identity. It's possible to have two mugs that look identical, but they are still separate, unique objects.

--------------------------------


## Objects

An object might contain other objects but they're still different objects. 

Objects also have characteristics that are used to describe them. For example, a car can be red or blue, a mug can be full or empty, and so on. These characteristics are also called attributes. An attribute describes the current state of an object. 

Objects can have multiple attributes (the mug can be empty, red and large). **The attribute describes the state of an object.**
An object's state is independent of its type; a cup might be full of water, another might be empty.

In the real world, each object behaves in its own way. The car moves, the phone rings, and so on. The same applies to objects - behavior is specific to the object's type.

So, the following three dimensions describe any object in object oriented programming: **identity**, **attributes**, **behavior**.

> An object is self-contained, with its own identity. It is separate from other objects. Each object has its own attributes, which describe its current state. Each exhibits its own behavior, which demonstrates what they can do.
> ![objects](https://api.sololearn.com/DownloadFile?id=2427)

---------------------------------------------------------------------------
## Class
**Objects are created using classes**, which are actually the focal point of OOP.

**The class describes what the object will be, but is separate from the object itself.** In other words, a class can be described as an object's blueprint, description, or definition.

**You can use the same class as a blueprint for creating multiple different objects**. For example, in preparation to creating a new building, the architect creates a blueprint, which is used as a basis for actually building the structure. That same blueprint can be used to create multiple buildings.

Programming works in the same fashion. We first define a class, which becomes the blueprint for creating objects.

**Each class has a name, and describes attributes and behavior.**

In programming, the term type is used to refer to a class name: We're creating an object of a particular type. Attributes are also referred to as properties or data.

### Methods

Method is another term for a class' behavior. A method is basically a function that belongs to a class.

Methods are similar to functions - they are blocks of code that are called, and they can also perform actions and return values.

### A Class Example

For example, if we are creating a banking program, we can give our class the following characteristics:
> name: BankAccount
attributes: accountNumber, balance, dateOpened
behavior: open(), close(), deposit()

The class specifies that each object should have the defined attributes and behavior. However, it doesn't specify what the actual data is; it only provides a definition.

**Once we've written the class, we can move on to create objects that are based on that class.** Each object is called an instance of a class. The process of creating objects is called *instantiation*.

Each object has its own identity, data, and behavior.

#### Declaring a Class

Begin your class definition with the keyword class. Follow the keyword with the class name and the class body, enclosed in a set of curly braces. 
The following code declares a class called BankAccount:
>class BankAccount { 
>
};

Define all attributes and behavior (or members) in the body of the class, within curly braces.

You can also define an **access specifier** for members of the class.
A member that has been defined using the **public** keyword can be accessed from outside the class, as long as it's anywhere within the scope of the class object.
You can also designate a class' members as **private** or **protected**. This will be discussed in greater detail later in the course.

```cpp
class BankAccount {
  public:
    void sayHi() {
      cout << "Hi" << endl;
    }
};
```

```cpp
int main() 
{
  BankAccount test;
  test.sayHi();
}
```

Our object named test has all the members of the class defined. 
Notice the dot separator (.) that is used to access and call the method of the object.
We must declare a class before using it, as we do with functions.

------------------------------

## Abstraction

**Data abstraction** is the concept of providing only essential information to the outside world. It's a process of representing essential features without including implementation details.

A good real-world example is a book: When you hear the term book, you don't know the exact specifics, i.e.: the page count, the color, the size, but you understand **the idea** of a book - the abstraction of the book.

The concept of abstraction is that we focus on essential qualities, rather than the specific characteristics of one particular example.

>Abstraction allows us to write a single bank account class, and then create different objects based on the class, for individual bank accounts, rather than creating a separate class for each bank account.
>![](https://api.sololearn.com/DownloadFile?id=2464)

----------------------------------------

## Encapsulation

Part of the meaning of the word encapsulation is the idea of "surrounding" an entity, not just to keep what's inside together, but also to **protect** it.

In object orientation, encapsulation means more than simply combining attributes and behavior together within a class; it also means *restricting access* to the inner workings of that class.

The key principle here is that an object only reveals what the other application components require to effectively run the application. *All else is kept out of view. *

This is called data hiding.

For example, if we take our BankAccount class, we do not want some other part of our program to reach in and change the balance of any object, without going through the deposit() or withdraw() behaviors.

We should hide that attribute, control access to it, so it is accessible only by the object itself.

This way, the balance cannot be directly changed from outside of the object and is accessible only using its methods.

This is also known as "black boxing", which refers to closing the inner working zones of the object, except of the pieces that we want to make public. This allows us to change attributes and implementation of methods without altering the overall program. For example, we can come back later and change the data type of the balance attribute.

In summary the **benefits of encapsulation** are:
- Control the way data is accessed or modified.
- Code is more flexible and easy to change with new requirements.
- Change one part of code without affecting other part of code.

-----------------------------

## Access Specifiers

Access specifiers are used to set access levels to particular members of the class. The three levels of access specifiers are **public**, **protected**, and **private**.

### Public
A public member is accessible from outside the class, and anywhere within the scope of the class object.

For example:
```cpp
#include <iostream>
#include <string>
using namespace std;

class myClass {
  public:
    string name;
};

int main() {
  myClass myObj;
  myObj.name = "SoloLearn";
  cout << myObj.name;
  return 0;
}

//Outputs "SoloLearn"
```

The name attribute is public; it can be accessed and modified from outside the code.

Access modifiers only need to be declared once; multiple members can follow a single access modifier.

Notice the colon (:) that follows the public keyword.


### Private

A private member cannot be accessed, or even viewed, from outside the class; it can be accessed only from within the class.
**A public member function may be used to access the private members**. For example:

```cpp
#include <iostream>
#include <string>
using namespace std;

class myClass {
  public:
    void setName(string x) {
      name = x;
    }
  private:
    string name;
};

int main() {
  myClass myObj;
  myObj.setName("John");

  return 0;
}
```
The name attribute is private and not accessible from the outside. The public setName() method is used to set the name attribute.

If no access specifier is defined, all members of a class are set to private by default.


We can add another public method in order to get the value of the attribute.
```cpp
class myClass {
  public:
    void setName(string x) {
      name = x;
    }
    string getName() {
      return name;
    }
  private:
    string name;
};
```
The getName() method returns the value of the private name attribute.


Putting it all together:

```cpp
#include <iostream>
#include <string>
using namespace std;
class myClass {
  public:
    void setName(string x) {
      name = x;
    }
    string getName() {
      return name;
    }
  private:
    string name;
};

int main() {
  myClass myObj;
  myObj.setName("John");
  cout << myObj.getName();

  return 0;
}

//Outputs "John"
```

We used encapsulation to hide the name attribute from the outside code. Then we provided access to it using public methods. Our class data can be read and modified only through those methods.

This allows for changes to the implementation of the methods and attributes, without affecting the outside code.


---------------------------------------------

## Constructors

Class constructors are special member functions of a class. They are executed whenever new objects are created within that class.

The constructor's **name is identical to that of the class**. It has no return type, not even void.
(kinda like __init__() in Python)
For example:
```cpp
class myClass {
  public:
    myClass() {
      cout <<"Hey";
    }
    void setName(string x) {
      name = x;
    }
    string getName() {
      return name;
    }
  private:
    string name;
};

int main() {
  myClass myObj;

  return 0;
}

//Outputs "Hey"
```

Now, upon the creation of an object of type myClass, the constructor is automatically called.


Constructors can be very useful for **setting initial values for certain member variables.**

A default constructor has *no parameters*. However, when needed, parameters can be added to a constructor. This makes it possible to assign an initial value to an object when it's created, as shown in the following example:
```cpp
class myClass {
  public:
    myClass(string nm) {
      setName(nm);
    }
    void setName(string x) {
      name = x;
    }
    string getName() {
      return name;
    }
  private:
    string name;
};
```
We defined a constructor, that takes one parameter and assigns it to the name attribute using the setName() method.


When creating an object, you now need to pass the constructor's parameter, as you would when calling a function:
```cpp
class myClass {
  public:
    myClass(string nm) {
      setName(nm);
    }
    void setName(string x) {
      name = x;
    }
    string getName() {
      return name;
    }
  private:
    string name;
};

int main() {
  myClass ob1("David");
  myClass ob2("Amy");
  cout << ob1.getName();
}
//Outputs "David"
```

We've defined two objects, and used the constructor to pass the initial value for the name attribute for each object.
It's possible to have multiple constructors that take different numbers of parameters.

--------------------
## Source & Header

The header file (.h) holds the function declarations (prototypes) and variable declarations. 

It currently includes a template for our new MyClass class, with one default constructor.

- MyClass.h

```cpp
#ifndef MYCLASS_H
#define MYCLASS_H

class MyClass
{
  public:
    MyClass();  //has been declared
  protected:
  private:
};

#endif // MYCLASS_H
```

The implementation of the class and its methods go into the source file (.cpp). Currently it includes just an empty constructor.

- MyClass.cpp

```cpp
#include "MyClass.h"

MyClass::MyClass()
{
   //ctor
}
```

### Scope Resolution Operator

The double colon in the source file (.cpp) is called the **scope resolution operator**, and it's used for the constructor definition:

```cpp
#include "MyClass.h"

MyClass::MyClass()
{
   //ctor
}
```

The scope resolution operator is used to define a particular class' member functions, which have **already been declared**. Remember that we defined the constructor prototype in the header file.
So, basically, MyClass::MyClass() refers to the MyClass() member function - or, in this case, constructor - of the MyClass class.


To use our classes in our main, **we need to include the header file** in the source file.(i.e.cpp) .

For example, to use our newly created MyClass in main:
```cpp
#include <iostream>
#include "MyClass.h"
using namespace std;

int main() {
  MyClass obj;
}
```

The header declares "what" a class (or whatever is being implemented) will do, while the cpp source file defines "how" it will perform those features.

-------------------------------------
## Destructors

> Recall **constructors**:    
> They're special member functions that are automatically called when an object is created.

Destructors are special functions, as well. They're called when an object is destroyed or deleted.

Objects are destroyed when they go out of scope, or whenever the delete expression is applied to a pointer directed at an object of a class.


The name of a destructor will be **exactly the same as the class**, only prefixed with a tilde (~). A destructor can't return a value or take any parameters.

```cpp
class MyClass {
  public: 
    ~MyClass() {
     // some code
    }
};
```
Destructors can be very useful for releasing resources before coming out of the program. This can include closing files, releasing memory, and so on.


After declaring the destructor in the header file, we can write the implementation in the source file MyClass.cpp:
即用header file来初始化， 用source file来具体实现。
```cpp
#include "MyClass.h"
#include <iostream>
using namespace std;

MyClass::MyClass()
{
  cout<<"Constructor"<<endl;
}

MyClass::~MyClass()
{
  cout<<"Destructor"<<endl;
}
```
Note that we included the <iostream> header, so that we can use cout.



Since destructors can't take parameters, they also can't be overloaded.  **Each class will have just one destructor.**

Defining a destructor is not mandatory; if you don't need one, you don't have to define one.

When the program runs, it first creates the object and calls the constructor. The object is deleted and the destructor is called when the program's execution is completed.

----------------------------------

## Selection Operator

### #ifndef & #define

We created separate header and source files for our class, which resulted in this header file.
```cpp
#ifndef MYCLASS_H
#define MYCLASS_H

class MyClass
{
  public:
  MyClass();
  protected:
  private:
};

#endif // MYCLASS_H 
```

**ifndef** stands for "if not defined". The first pair of statements tells the program **to define the MyClass header file if it has not been defined already**. **endif **ends the condition.

This* prevents a header file from being included more than once within one file.*

-------------------------------------------------


## Member Functions

Let's create a sample function called myPrint() in our class. 

MyClass.h
```cpp
class MyClass
{
  public:
   MyClass();
   void myPrint();
};
```

MyClass.cpp
```cpp
#include "MyClass.h"
#include <iostream>
using namespace std;

MyClass::MyClass() {
}

void MyClass::myPrint() {
  cout <<"Hello"<<endl;
}
```

Since myPrint() is a regular member function, **it's necessary to specify its return type in both the declaration and the definition.**

--------------------

## Dot Operator

Next, we'll create an object of the type MyClass, and call its myPrint() function using the dot (.) operator:

```cpp
#include "MyClass.h"

int main() {
  MyClass obj;
  obj.myPrint();
}

// Outputs "Hello"
```

--------------------------

## Pointers

We can also use a pointer to access the object's members. 
The following pointer points to the obj object:

```cpp
MyClass obj;
MyClass *ptr = &obj;
```

The **type of the pointer is MyClass**, as **it points to an object of that type.**
指针的类型 是 其所指变量/对象的类型。

### Selection Operator

The arrow member selection operator (->) is used to **access an object's members with a pointer.**
```cpp
MyClass obj;
MyClass *ptr = &obj;
ptr->myPrint();
```

- When working with an **object**, use the **dot member selection** operator (.).
- When working with **a pointer to the object**, use the **arrow member selection** operator (->).

---------------------------

## Constants

A constant is an expression with a fixed value. It cannot be changed while the program is running.
Use the const keyword to define a constant variable.
> const int x = 42;

All constant variables must be initialized at the time of their creation.


## Constant Objects

As with the built-in data types, we can** make class objects constant by using the const keyword**.
> const MyClass obj;

All const variables must be initialized when they're created. In the case of classes, this initialization is done via **constructors**. If a class is not initialized using a parameterized constructor, a public default constructor must be provided - if no public default constructor is provided, a compiler error will occur.

**Once a const class object has been initialized via the constructor, you cannot modify the object's member variables.** This includes both directly making changes to public member variables and calling member functions that set the value of member variables. When you've used const to declare an object, you can't change its data members during the object's lifetime.


**Only non-const objects can call non-const functions.**
A constant object can't call regular functions. Hence, for a constant object to work you need a constant function. 

To specify a function as a const member, the const keyword must follow the function prototype, outside of its parameters' closing parenthesis. For const member functions that are defined outside of the class definition, **the const keyword must be used on both the function prototype and definition**. For example:

MyClass.h
```cpp
class MyClass
{
  public:
    void myPrint() const;
};
```

MyClass.cpp
```cpp
#include "MyClass.h"
#include <iostream>
using namespace std;

void MyClass::myPrint() const {
  cout <<"Hello"<<endl;
}
```

Now the **myPrint() function is a constant member function**. As such, it can be called by our constant object:
```cpp
int main() {
  const MyClass obj;
  obj.myPrint();
}
// Outputs "Hello"
```

**Attempting to call a regular function from a constant object results in an error.**   (const call const)

In addition, a compiler error is generated when any const member function attempts to change a member variable or to call a non-const member function.

**Defining constant objects and functions ensures that corresponding data members cannot be unexpectedly modified.**


--------------------------------------------------------
## Member Initializers

Recall that constants are variables that cannot be changed, and that all const variables must be initialized at time of creation.

C++ provides a handy syntax for initializing members of the class called the member initializer list (also called a **constructor initializer**).


Consider the following class:
```cpp
class MyClass {
  public:
   MyClass(int a, int b) {
    regVar = a;
    constVar = b;  //error line
   }
  private:
    int regVar;
    const int constVar;
};
```

This class has **two member variables**, regVar and constVar. It also has a constructor that takes two parameters, which are used to initialize the member variables.


Running this code returns an **error**, because one of its member variables is a constant, **which cannot be assigned a value after declaration**.

In cases like this one**, a member initialization list can be used to assign values to the member variables**.
```cpp
class MyClass {
 public:
  MyClass(int a, int b)
  : regVar(a), constVar(b)
  {
  }
 private:
  int regVar;
  const int constVar;
};
```
Note that in the syntax, the initialization list follows the constructor parameters. The list begins with a colon (:), and then lists each variable to be initialized, along with the value for that variable, with a comma to separate them. 

Use the syntax **variable(value)** to assign values.

The initialization list eliminates the need to place explicit assignments in the constructor body. Also, the initialization list **does not end with a semicolon**.


Let's write the previous example using separate header and source files.

MyClass.h
```cpp
class MyClass {
  public:
   MyClass(int a, int b);
  private:
   int regVar;
   const int constVar;
};
```

MyClass.cpp
```cpp
MyClass::MyClass(int a, int b)
: regVar(a), constVar(b)
{
  cout << regVar << endl;
  cout << constVar << endl;
}
```

We have added cout statements in the constructor to print the values of the member variables.
Our next step is to create an object of our class in main, and use the constructor to assign values.

```cpp
#include "MyClass.h"

int main() {
  MyClass obj(42, 33);
}

/*Outputs 
42
33
*/
```

The constructor is used to create the object, assigning two parameters to the member variables via the member initialization list.

**The member initialization list may be used for regular variables, and must be used for constant variables.** Even in cases in which member variables are not constant, it makes good sense to use the member initializer syntax.

----------------------------


## Composition

In the real world, complex objects are typically built using smaller, simpler objects. For example, a car is assembled using a metal frame, an engine, tires, and a large number of other parts. This process is called composition.

In C++, object composition involves using classes as member variables in other classes.
T
his sample program demonstrates composition in action. It contains **Person** and **Birthday** classes, and each Person will have a Birthday object as its member.

- Step1:
Birthday:
```cpp
class Birthday {
 public:
  Birthday(int m, int d, int y)
  : month(m), day(d), year(y)
  { 
  }
 private:
   int month;
   int day;
   int year;
};
```
Our Birthday class has three member variables. It also has a constructor that initializes the members using a member initialization list.

The class was declared in a single file for the sake of simplicity. Alternatively, you could use header and source files.


- Step2: Add a printDate() function to our Birthday class:
```cpp
class Birthday {
 public:
  Birthday(int m, int d, int y)
  : month(m), day(d), year(y)
  {
  }
  void printDate()
  {
   cout<<month<<"/"<<day
   <<"/"<<year<<endl;
  }
 private:
  int month;
  int day;
  int year;
};
```

- Step 3: Next, we can create the Person class, which includes the Birthday class.

```cpp
#include <string>
#include "Birthday.h"

class Person {
 public:
  Person(string n, Birthday b)
  : name(n),
   bd(b)
  {
  }
 private:
  string name;
  Birthday bd;
};
```

The Person class has a name and a Birthday member, and a constructor to initialize them. Ensure that the corresponding header files are included.

**Composition** is used for objects that share a ** has-a** relationship, as in "A Person has a Birthday".

- Step 4: Add a printInfo() function to our Person class, that prints the data of the object:

```cpp
class Person {
 public:
  Person(string n, Birthday b)
  : name(n),
  bd(b)
  {
  }
  void printInfo()
  {
   cout << name << endl;
   bd.printDate();
  }
 private:
  string name;
  Birthday bd;
};
```
Notice that we can call the **bd **member's **printDate()** function, since it's of type **Birthday**, which has that function defined.

- Step 5: Now that we've defined our Birthday and Person classes, we can go to our main, create a Birthday object, and then pass it to a Person object.

```cpp
int main() {
  Birthday bd(2, 21, 1985);
  Person p("David", bd);
  p.printInfo();
}

/*Outputs
David
2/21/1985
*/
```

We've created a **Birthday** object for the date of 2/21/1985. Next, we created a **Person **object and passed the Birthday object to its constructor. Finally, we used the **Person object's printInfo()** function to print its data.

In general, **composition** serves to keep each individual class relatively simple, straightforward, and focused on performing one task. It also enables each sub-object to be self-contained, allowing for reusability (we can use the Birthday class within various other classes).

---------------------------------------

## Friend Functions

Normally, private members of a class cannot be accessed from outside of that class.

However, **declaring a non-member function as a friend of a class** allows it to access the class' private members. This is accomplished by **including a declaration of this external function within the class, and preceding it with the keyword friend. **

In the example below, **someFunc()**, which is not a member function of the class, is a friend of MyClass and can access its private members.
```cpp
class MyClass {
 public:
  MyClass() {
   regVar = 0;
  }
 private:
  int regVar;
    
  friend void someFunc(MyClass &obj);
};
```

**Note that when passing an object to the function, we need to pass it by reference, using the & operator.**


The function someFunc() is defined as a regular function outside the class. **It takes an object of type MyClass as its parameter**, and is able to access the private data members of that object.
```cpp
class MyClass {
 public:
  MyClass() {
   regVar = 0;
  }
 private:
  int regVar;
    
 friend void someFunc(MyClass &obj); //declare in the class as a friend
};
//define outside of the class, has access to private
void someFunc(MyClass &obj) { 
  obj.regVar = 42;
  cout << obj.regVar;
}
```
The someFunc() function changes the private member of the object and prints its value.

To make its members accessible, **the class has to declare the function as a friend in its definition**. You cannot "make" a function a friend to a class without the class "giving away" its friendship to that function.


Now we can create an object in main and call the someFunc() function:
```cpp
int main() {
  MyClass obj;
  someFunc(obj);
}

//Outputs 42
```

someFunc() had the ability to modify the private member of the object and print its value.

Typical use cases of friend functions are operations that are conducted between two different classes accessing private members of both. 

You can declare a function friend across any number of classes.
Similar to **friend functions**, you can define a **friend class**, which has access to the private members of another class.


------------------------------------------
## This

Every object in C++ has access to its own address through an important pointer called the** this pointer**.

Inside a member function **this** may be used to refer to the invoking object.

```cpp
class MyClass {
 public:
  MyClass(int a) : var(a)
  { }
 private:
  int var;
};
```
**Friend functions do not have a this pointer**, because friends are not members of a class.

The **printInfo()** method offers three alternatives for printing the member variable of the class.
```cpp
class MyClass {
 public:
  MyClass(int a) : var(a)
  { }
  void printInfo() {
   cout << var<<endl;
   cout << this->var<<endl;  //arrow selection
   cout << (*this).var<<endl; //(*this) = object
  }
 private:
  int var;
};
```

All three alternatives will produce the **same result**.
**this** is a **pointer to the object**, so the arrow selection operator is used to select the member variable.

Note that **only member functions have a this pointer.**

------------------------------

## Operator Overloading

Most of the C++ built-in operators can be redefined or overloaded. 
Thus, operators can be used with user-defined types as well (for example, allowing you to add two objects together).

This chart shows the operators that can be overloaded.
![operator overloading](https://api.sololearn.com/DownloadFile?id=2463)


> Operators that can't be overloaded include :: | .* | . | ?:

A sample class to demonstrate operator overloading:
```cpp
class MyClass {
 public:
  int var;
  MyClass() {}
  MyClass(int a)
  : var(a) { }
};
```

Our class has **two constructors **and **one member variable**: var.
We will be overloading the **+ operator**, to enable adding two objects of our class together.


**Overloaded operators are functions**, defined by the keyword **operator** followed by the symbol for the operator being defined.
An overloaded operator is similar to other functions in that it **has a return type and a parameter list**.

In our example we will be overloading the + operator. It will return an object of our class and take an object of our class as its parameter.
```cpp
class MyClass {
 public:
  int var;
  MyClass() {}
  MyClass(int a)
  : var(a) { }

  MyClass operator+(MyClass &obj) {
  }
};
```
Overload operator "+", returns MyClass type, and takes in MyClass object as parameter.   
(Note: **passing object to function, need to use &**)


We need our **+ operator** to **return a new MyClass object ** with a member variable equal to the **sum of the two objects' member variables.**
```cpp
class MyClass {
 public:
  int var;
  MyClass() {}
  MyClass(int a)
  : var(a) { }

  MyClass operator+(MyClass &obj) {
   MyClass res;
   res.var= this->var+obj.var;
   return res; 
  }
};
```

Here, we declared a new **res** object. We then assigned the sum of the member variables of the current object (this) and the parameter object (obj) to the res object's var member variable. The res object is returned as the result.

This gives us the ability to *create objects in main and use the overloaded + operator to add them together*.
