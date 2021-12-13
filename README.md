# usage of const and & operator

## The const keyword allows you to specify whether or not a variable is modifiable. You can use const to prevent modifications to variables and const pointers and const references prevent changing the data pointed to 

## the const keyword provides guarantees to your users that allow you to make performance optimizations without the threat of damaging their data

## The const keyword specifies that a variable's value is constant and tells the compiler to prevent the programmer from modifying it.

// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // not available
   i++;   // not available
}


## you can use the const keyword instead of the #define preprocessor directive to define constant values

## you can specify the size of an array with a const variable as follows:

const int maxarray = 255;
char store_char[maxarray];
The const keyword can also be used in pointer declarations.
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   
   aptr = yourbuf;   
}

## A pointer to a variable declared as const can be assigned only to a pointer that is also declared as const.

#include <stdio.h>
int main() {
   const char *mybuf = "test";
   char *yourbuf = "test2";
   printf_s("%s\n", mybuf);

   const char *bptr = mybuf; 
   printf_s("%s\n", bptr);

   }

## You can use pointers to constant data as function parameters to prevent the function from modifying a parameter passed through a pointer.

## For objects that are declared as const, you can only call constant member functions. This ensures that the constant object is never modified.

birthday.getMonth();    // Okay
birthday.setMonth( 4 );    // Error


## The unary address-of operator (&) returns the address of its operand.

## The following code fragment shows how the address-of operator result differs, depending on whether a class member is static:

class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}

## Applying the address-of operator to a reference type gives the same result as applying the operator to the object to which the reference is bound. For example:

#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
Output:
&d equals &rd

## The following example uses the address-of operator to pass a pointer argument to a function:

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
Output:
25

