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


# Week 2
## Blocks and Scope

* Variable Scope: Variables declared within a block have that block as their scope. This means they are only accessible within the block in which they are declared. For example:

'''{
    int a;
    // 'a' is only accessible within this block
}
'''

