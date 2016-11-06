You Don't Know JS: Types & Grammar Notes:

Chapter 1: Types:


Javascript has 7 types:
-------------------------------------------------------------------------------

* Null
* Undefined
* Boolean
* String
* Number
* Object
* Symbol (new in ES6)

All of these are primitives except objects.

The typeof operator works to identify these types well enough with the
exception of null.  


NULL:
-------------------------------------------------------------------------------

If you do a typeof operator to identify null you will get an "object".
Null is the only primitive value that is 'falsy'.

// Fun fact:
The seventh string value that typeof returns is function! Also the .length of
a function is the different number of values it has!
//


Undefined vs Undeclared:
-------------------------------------------------------------------------------

This is confusing one, often undeclared is mistaken for undefined; due to
certain coding traits of js as well as browsers being misinformative.

Simply put, 'undefined is a value that a declared variable can hold.
"Undeclared" means a variable has never been declared'

//Example:

var a = 8;
var b;

a is defined as 8, a number.
b is undefined.
thisIsNotAVar is undeclared because it was never declared.
//

So why don't they fix it and make it undeclared. Other than breaking a crap ton
of codes that exists we can use this odd fact about undeclared to create safety
guards are that useful.
