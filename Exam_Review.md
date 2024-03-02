# Week 1
## Fundamentals

* Define the variables before input.

double x;
cin >> x;

* Variable Names

Case sensitive, consists of letters, numbers and _, starting with a letter or _, can’t use reserved words

* Type Casting

Type casting to solve the problem with integer division.

  * answer = double(numerator) / denominator;
  
  Do NOT use
  
  * answer = double(numerator / denominator);

  Eg. double (5 / 2) 
  
  In this example, the result will be 2.0 instead of the expected 2.5. This is because numerator / denominator performs integer division, resulting in 2, and only then is it cast to a double.


## Libraries in This Module

<cmath> - library with mathematical functions

<iostream> - links the library to our cod


# Week 2
## Blocks and Scope

* Variable Scope: Variables declared within a block have that block as their scope. This means they are only accessible within the block in which they are declared. For example:

```
{
    int a;
    // 'a' is only accessible within this block
}
```

Another example: 

```
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


* Increment

```
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

* Value Range

(y2 >= -0.5 && y2 < 0.3)

** cannot be (-0.5 < y2 < 0.3), because  -0.5 < y2 is 1 and 1 < 0.3 is always true **


(y3 >= 0.001 && y3 <= 0.01 || y3>= 100) 

or ((y3 >= 0.001 && y3 <= 0.01) || (y3>= 100))

&& is prior to ||, it can also be (y3>= 100 || y3 >= 0.001 && y3 <= 0.01)











