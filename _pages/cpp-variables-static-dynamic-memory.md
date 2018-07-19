---
permalink: /cpp/variables
layout: single
classes: wide
title:  "Variables"
tags: [C++, notes]
date:   2018-07-19
sidebar:
  nav: "cpp"
---



# Variabeles
-----------------------------------
## Signed and unsigned
Several of the basic types, including integers, can be modified using one or more of these type modifiers: 
- signed: A signed integer can hold **both negative and positive **numbers.
- unsigned: An unsigned integer can hold **only positive **values.

## Short and long
- short: Half of the default size.
- long: Twice the default size.

## Floating Point Numbers

A floating point type variable can hold a real number, such as 420.0, -3.33, or 0.03325. The words floating point refer to the fact that a varying number of digits can appear before and after the decimal point. You could say that the decimal has the ability to "float". 

There are three different floating point data types: **float, double, and long double.**

In most modern architectures, a float is 4 bytes, a double is 8, and a long double can be equivalent to a double (8 bytes), or 16 bytes.
```python
double temp = 4.21;
```

Floating point data types are always** signed**, which means that they have the capability to hold both positive and negative values.

## "Strings"
A string is an ordered sequence of characters, enclosed in **double quotation marks**

## 'Char'
A char variable holds a **1-byte** integer. However, instead of interpreting the value of the char as an integer, the value of a char variable is typically interpreted as an **ASCII character**.

## Arrays
An array as a collection of variables that are all of the same type.

When declaring an array, specify its element types, **as well as the number of elements it will hold**. 

```python
int a[5];
int b[5] = {11, 45, 62, 70, 88};
```

## Pointers
Every variable is a memory location, which has its address defined. 

That address can be accessed using the ampersand (&) operator (also called the address-of operator), which denotes an address in memory.
### Definition
**A data type that contains an address.** i.e.
>a pointer is a **variable**, with the address of another variable as its value.
(指针是用来存 另一个变量地址的 变量)
In C++, pointers help make certain tasks easier to perform. Other tasks, such as dynamic memory allocation, cannot be performed without using pointers.

All pointers share the same data type - a long hexadecimal number that represents a memory address.

The only difference between pointers of different data types is the data type of the variable that the pointer points to.

### Declaration
A pointer is a variable, and like any other variable, it must be declared before you can work with it. The **asterisk(*)** sign is used to declare a pointer (the same asterisk that you use for multiplication), however, in this statement the asterisk is being used to designate a variable as a pointer. 

Following are valid pointer declarations:

```
int *ip;  // pointer to an integer
double *dp;   // pointer to a double
float *fp;  // pointer to a float
char *ch;  // pointer to a character
```

Just like with variables, we give the pointers a name and define the type, to which the pointer points to. （指针的类型即是其包含的地址所代表的变量的类型）
The asterisk sign can be placed next to the data type, or the variable name, or in the middle.

### Using Pointers

Here, we assign the address of a variable to the pointer.
```
int score = 5;
int *scorePtr; //定义一个指针
scorePtr = &score; // 该指针指向score这个变量所在地址: scorePtr = address of score

cout << scorePtr << endl;

//Outputs "0x29fee8"
```

The code above declares a pointer(called scorePtr) to an integer, and assigns to it the memory location of the score variable using the ampersand (&: address-of) operator.
Now, **scorePtr's value is the memory location of score**.

### Pointer Operations

There are two operators for pointers:
- Address-of operator (&): returns the memory address of its operand. 
- Contents-of (or dereference) operator (*): returns the value of the variable located at the address specified by its operand.

For example:
```
int var = 50;
int  *p;
p = &var;

cout << var << endl;
// Outputs 50 (the value of var)

cout << p << endl;
// Outputs 0x29fee8 (var's memory location)

cout << *p << endl;
/* Outputs 50 (the value of the variable
 stored in the pointer p) */
```

The asterisk ($$*$$) is used in declaring a pointer for the simple purpose of indicating that it is a pointer (The asterisk is part of its type compound specifier). 
Don't confuse this with the **dereference operator**, which is used to o**btain the value located at the specified address**. They are simply two different things represented with the same sign.

-----------------------------------------
# Static & Dynamic Memory

To be successful as a C++ programmer, it's essential to have a good understanding of how dynamic memory works.

In a C++ program, memory is divided into two parts:
- The **stack**: All of your local variables take up memory from the stack.
- The **heap**: Unused program memory that can be used when the program runs to dynamically allocate the memory.

Many times, you are not aware in advance how much memory you will need to store particular information in a defined variable and the size of required memory can be determined at run time.

You can allocate memory at run time within the heap for the variable of a given type using the **new **operator, which returns the address of the space allocated.
```
new int; //用于分配地址，是地址，地址， 地址。
```

This allocates the memory size necessary for* storing an integer on the **heap***, and returns that address.

## Dynamic Memory

The **allocated address can be stored in a pointer**, which can then be dereferenced to access the variable.

Example:
```
int *p = new int;  //assign memory on the heap 
*p = 5; //dereference
```

We have **dynamically allocated memory for an integer, and assigned it a value of 5**.

The pointer *p is stored in the stack* as a local variable, and holds the heap's allocated address as its value. The *value of 5 is stored at that address in the heap.*

For local variables on the stack, managing memory is carried out automatically.
On the heap, it's necessary to manually handle the dynamically allocated memory, and use the delete operator to free up the memory when it's no longer needed.
```
delete pointer; // free memory on the heap after use
```
This statement releases the memory pointed to by pointer.

For example:
```
int *p = new int; // request memory
*p = 5; // store value

cout << *p << endl; // use value

delete p; // free up the memory
```

#### Dangling Pointers
**Pointers that are left pointing to non-existent memory locations are called dangling pointers**.

The delete operator frees up the memory allocated for the variable, but does not delete the pointer itself, as the pointer is stored on the stack.
（free 了heap的内存，但是包含原地址的pointer并没有被delete）

For example:
```
int *p = new int; // request memory
*p = 5; // store value

delete p; // free up the memory
// now p is a dangling pointer

p = new int; // reuse for a new address
```

#### NULL pointer
The NULL pointer is a constant with a value of zero that is defined in several of the standard libraries, including iostream. 

It's a good practice to assign NULL to a pointer variable when you declare it, in case you do not have exact address to be assigned. 

A pointer assigned NULL is called a **null pointer**. For example: 
```
int *ptr = NULL;
```

### Dynamic memory  for arrays
  
For example: 
```
int *p = NULL; // Pointer initialized with null
p = new int[20]; // Request memory
delete [] p; // Delete array pointed to by p
```
Note the brackets in the syntax.

Dynamic memory allocation is useful in many situations, such as when your program depends on input. As an example, when your program needs to read an image file, it doesn't know in advance the size of the image file and the memory necessary to store the image.

## Sizeof()
![size of variables](https://api.sololearn.com/DownloadFile?id=2460)
The sizeof operator can be used to get a variable or data type's size, in bytes.
Syntax: sizeof (data type)
e.g.
```
cout << "char: " << sizeof(char) << endl;
cout << "int: " << sizeof(int) << endl;
cout << "float: " << sizeof(float) << endl;
cout << "double: " << sizeof(double) << endl;
int var = 50;
cout << "var: " << sizeof(var) << endl;

/* Outputs
char: 1
int: 4
float: 4
double: 8
var: 4
*/ 
```

### sizeof array

The C++ **sizeof()** operator is also used to determine the size of an array.
For example:
```
double myArr[10];
cout << sizeof(myArr) << endl; 
//Outputs 80
```
Explanation: On our machine, **double takes 8 bytes**. The array stores 10 doubles, so the entire array occupies 80 = (8*10) bytes in the memory. 

In addition, divide the total number of bytes in the array by the number of bytes in a single element to learn how many elements you have in the array.

For example:
```
int numbers[100];
cout << sizeof(numbers) / sizeof(numbers[0]);
// Outputs 100
```

