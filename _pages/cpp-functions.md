---
permalink: /cpp/functions
layout: single
classes: wide
title:  "Functions"
tags: [C++, notes]
date:   2018-07-19
sidebar:
  nav: "cpp"
---

------------------------------------
## Define a function
Define a C++ function using the following syntax:

>return_type function_name( parameter list )
{
   body of the function
}

- **return-type**: Data type of the value returned by the function.
- **function name**: Name of the function.
- **parameters**: When a function is invoked, you pass a value to the parameter. This value is referred to as actual parameter or argument. The parameter list refers to the type, order, and number of the parameters of a function. 
-** body of the function**: A collection of statements defining what the function does. 

## Random Numbers

Being able to generate random numbers is helpful in a number of situations, including when creating games, statistical modeling programs, and similar end products. 

In the C++ standard library, you can access a pseudo random number generator function that's called **rand()**. When used, we are required to include the header **<cstdlib>.**
```cpp
#include <iostream>
#include <cstdlib>
using namespace std;

int main() {
  cout << rand();
}
```

## The srand() Function

The srand() function is used to generate truly random numbers.

This function allows to specify a seed value as its parameter, which is used for the rand() function's algorithm.
```cpp
int main () {
  srand(98);

  for (int x = 1; x <= 10; x++) {
    cout << 1 + (rand() % 6) << endl;
  }
}
```


A solution to generate truly random numbers, is to **use the current time as a seed value** for the srand() function.
This example makes use of the time() function to get the number of seconds on your system time, and randomly seed the rand() function (we need to include the <ctime> header for it):
```
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main () {
  srand(time(0));

  for (int x = 1; x <= 10; x++) {
    cout << 1 + (rand() % 6) << endl;
  }
}
```

**time(0)** will return the current second count, prompting the srand() function to set a different seed for the rand() function each time the program runs.

Using this seed value will create a different output each time we run the program.

>**Note: Function overloading**
You can not overload function declarations that differ only by return type.
The following declaration results in an error.


## Recursion

A recursive function in C++ is a function that calls itself.

To avoid having the recursion run indefinitely, you must include a termination condition.

```cpp
// calculate factorial 
int factorial(int n) {
  if (n==1) {
    return 1;
  }
  else {
    return n * factorial(n-1);
  }
}
int main() {
  cout << factorial(5);
}

//Outputs 120
```


## Arrays and Functions

An array can also be passed to a function as an argument. 

The parameter should be defined as an array using **square brackets[]**, when declaring the function. 

For example:
```cpp
void printArray(int arr[], int size) {
  for(int x=0; x<size; x++) {
    cout <<arr[x];
  }
}
```

We can use our function in main(), and call it for our sample array:
```cpp
void printArray(int arr[], int size) {
  for(int x=0; x<size; x++) {
    cout <<arr[x]<< endl;
  }
}
int main() {
  int myArr[3]= {42, 33, 88};
  printArray(myArr, 3);  //array's name without [] when passing as an argument
}
```

The printArray function takes an array as its parameter (int arr[]), and iterates over the array using a for loop.

We call the function in main(), which is where we pass the myArr array to the function, which prints its elements.

Remember to specify the array's name without square brackets when passing it as an argument to a function.


## Function Arguments

There are two ways to pass arguments to a function as the function is being called.

- **By value**: This method copies the argument's actual value into the function's formal parameter. Here, we can make changes to the parameter within the function without having any effect on the argument.

- ** By reference**: This method copies the argument's reference into the formal parameter. Within the function, the reference is used to access the actual argument used in the call. This means that any change made to the parameter affects the argument.
By default, C++ uses call by value to pass arguments.

### Passing by Value

By default, arguments in C++ are passed by value.
When passed by value, a copy of the argument is passed to the function.

Example:
```cpp
void myFunc(int x) {
  x = 100;
}

int main() {
  int var = 20;
  myFunc(var);
  cout << var;
}
// Outputs 20
```
Because a copy of the argument is passed to the function, the original argument is not modified by the function.

### Passing by Reference

Pass-by-reference **copies an argument's address** into the formal parameter. Inside the function, the address is used to access the actual argument used in the call. This means that changes made to the parameter affect the argument.
To pass the value by reference, argument pointers are passed to the functions just like any other value.
```cpp
void myFunc(int *x) {
  *x = 100;
}

int main() {
  int var = 20;
  myFunc(&var);
  cout << var;
}
// Outputs 100
```

As you can see, we passed the variable directly to the function using the address-of operator &.  The function declaration says that the function takes a pointer as its parameter (defined using the * operator).

As a result, **the function has actually changed the argument's value**, as accessed it via the pointer.


#### Summary

- Passing by **value**: This method copies the actual value of an argument into the formal parameter of the function. In this case, changes made to the parameter inside the function have no effect on the argument.

- Passing by **reference**: This method copies the reference of an argument into the formal parameter. Inside the function, the reference is used to access the actual argument used in the call. So, changes made to the parameter also affect the argument.

In general, **passing by value is faster and more effective**. Pass by reference when your function needs to modify the argument, or when you need to pass a data type, that uses a lot of memory and is expensive to copy.