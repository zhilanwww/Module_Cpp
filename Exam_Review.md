[TOC]
# Week 1
## Fundamentals

Define the variables before input.

double x;

cin >> x;

## Variable Names

Case sensitive, consists of letters, numbers and _, starting with a letter or _, can’t use reserved words

## Type Casting

Type casting to solve the problem with integer division.

  * answer = double(numerator) / denominator;
  
  Do NOT use
  
  * answer = double(numerator / denominator);

 Eg. double (5 / 2) 
  
 In this example, the result will be 2.0 instead of the expected 2.5. This is because numerator / denominator performs integer division, resulting in 2, and only then is it cast to a double.


## Libraries in This Module

Use #include + \<*library name*\>

\<cmath\> - library with mathematical functions

\<iostream\> - links the library to our cod

\<fstream\> - Using \<fstream\> instead of \<iostream\> and object of stream to write into a file instead of the screen.


# Week 2
## Blocks and Scope

* Variable Scope: Variables declared within a block have that block as their scope. This means they are only accessible within the block in which they are declared. For example:

```cpp
{
    int a;
    // 'a' is only accessible within this block
}
```

Another example: 

```cpp
#include <iostream>
using namespace std;

int i1 = 1, i2 = 2, i3 = 3;

int main() {
    i1 = i2 + i3;
    i2 = i1 * i3;
    cout << i1 << "\t" << i2 << "\t" << i3 << endl;

    {
        i3 = i1 + 2;
        cout << i1 << "\t" << i2 << "\t" << i3 << endl;

        {
            i2 = ++i3;
            cout << i1 << "\t" << i2 << "\t" << i3 << endl;
        }
    }

    return 0;
}
```

Output: 

5       15      3

5       15      7

5       8       8


## Increment

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 3;

    cout << ++a << endl;   // Pre-increment: increments 'a' and then prints the result (4)
    cout << a << endl;     // Prints the current value of 'a' (4)
    cout << a++ << endl;   // Post-increment: prints the current value of 'a' and then increments it (4, then increments to 5)
    cout << a << endl;     // Prints the updated value of 'a' after post-increment (5)

    return 0;
}
```

## Value Range

(y2 >= -0.5 && y2 < 0.3)

cannot be (-0.5 < y2 < 0.3), because  -0.5 < y2 is 1 and 1 < 0.3 is always true

(y3 >= 0.001 && y3 <= 0.01 || y3>= 100) 

or ((y3 >= 0.001 && y3 <= 0.01) || (y3>= 100))

&& is prior to ||, it can also be (y3>= 100 || y3 >= 0.001 && y3 <= 0.01)


# Week 3
## Loops

In a do-while loop, the statements inside the loop are executed first, and then the condition is checked. 

So, do-while loop first runs the statements and then checks for the condition, thus always performing **at least ONE** iteration.

```cpp
#include <iostream>

int main() {
    int n = 10;

    do {
        std::cout << --n << " ";
    } while (n > 0);

    return 0;
}
// Output: 9 8 7 6 5 4 3 2 1 0
```

```cpp
#include <iostream>

int main() {
    int n = 10;

    do {
        std::cout << n-- << " ";
    } while (n > 0);

    return 0;
}
// Output: 10 9 8 7 6 5 4 3 2 1
```

## Continue and Break
continue - jumps to the next iteration

break - stops the loop immediately

Eg. Prime Number
```cpp
#include <iostream>
using namespace std;
int main()
{
	int n;
	cin >> n;
	bool isprime = true;
	for (int i=2; i<n/2; i++)
	{
		if (n % i == 0) 
			isprime = false;
			break;
		}
	}
	cout << n << " is " << ((isprime) ? "" : "NOT ") << "prime\n";
	return 0;
}
```

# Week 4
## Polymorphism

We often want to reuse compiled code, e.g. libraries. We can create our own libraries as follows.

Decompose the code into *header* and *source* files.

```cpp
#ifndef CDF_H
#define CDF_H

float cdf(float); // A function must be declared before being used. Function declarations end with a ;

#endif
```
Create "average.cpp" with function files.

Do not forget to include any libraries you use.

In "main.cpp" add ```#include "cdf.h"```

Compile all relevant ".cpp" files


# Week 5
## Passing by Value / Reference

A new copy of the variable is created for each function call. That copy has the function as its scope and thus the original variable is not affected.

When a variable is passed to a function by value in programming languages like C++, a new copy of that variable is created within the function's scope. This means that the function receives a copy of the original variable's value, not the actual variable itself. The term "by value" indicates that the function operates on its own local copy of the variable's value.

Here's what happens in more detail:

1. Function Call: When you call a function and pass a variable by value, the function creates a new local variable with the same value as the original variable.

2. Local Scope: The newly created variable is local to the function, meaning it only exists within the function's block of code. Any changes made to this local variable do not affect the original variable outside the function.

3. Scope Isolation: The function operates on its local copy of the variable without impacting the original variable. Changes made within the function, such as modifications or assignments to the variable, are confined to the function's scope.

```cpp
// Passing the Value
#include <iostream>

int factorial(int number) {
    int product = 1;
    for (; number > 0; number--) {
        product *= number;
    }
    return product;
}

int main() {
    int value = 5;
    int result = factorial(value); // Example usage with 5!
    std::cout << "Factorial: " << result << std::endl;
    std::cout << "Original value after function: " << value << std::endl; 
    return 0;
}
/* 
Output:
Factorial: 120
Original value after function: 5 
*/
```

In the case of passing by reference, the function receives the actual variable itself, not a copy. Therefore, any changes made to the variable inside the function will directly affect the original variable. Here's the provided example in C++:

```cpp
// Passing the Reference
#include <iostream>

int factorialRef(int& number) {
    int product = 1;
    for (; number > 0; number--) {
        product *= number;
    }
    return product;
}

int main() {
    int value = 5;
    int result = factorialRef(value); // Example usage with passing by reference
    std::cout << "Factorial: " << result << std::endl;
    std::cout << "Original value after function: " << value << std::endl;  // value is changed
    return 0;
}
/* 
Output:
Factorial: 120
Original value after function: 0 
*/
```
## Array
If we don't define all the elements of array, the remaining will be zeros.

```cpp
int arr[5] = {1};
```

The first element of arr is 1, the rest of it is 0.

We can use `typedef` for compactness:

```cpp
typedef double array[10];
```

This creates a new type named `array`, which is an array of 10 `double` values. After defining this type, you can use it to declare variables:

```cpp
array A;
// equivalent to: double A[10];
```

## Out of Bounds
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
	int arr[5] = {1,2,3};
	for (int i=0; i<5; ++i)
		cout << i << "\t" << arr[i] << "\t" << sqrt(arr[i]) << endl;
	cout << arr[100] << endl;
	cout << arr[10000] << endl;
	return 0;
}
```
0       1       1
1       2       1.41421
2       3       1.73205
3       0       0
4       0       0
34604096
28239

In the given C++ code, the array `arr` is declared with a size of 5, but you are trying to access elements at indices 100 and 10000. This will result in undefined behavior since those indices are out of bounds for the array. Accessing elements beyond the array's bounds can lead to unpredictable consequences, and the program might crash or produce unexpected results.

The specific output cannot be predicted, and it is considered undefined behavior. It may vary depending on the compiler and platform.



























