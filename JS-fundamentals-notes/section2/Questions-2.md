1. Explain lexical scope in your own words

Lexical scope is how variables are defined in multiple levels of functions.
For example the inner function contains the scope of it's parent's function.
Therefore it goes from the inner to outer to find all the necessary information
to make that function work.

2. Understand how variables are accessed within nested scopes

Variables in nested scopes can be accessed within that scope or it's parents
(or parent's parent's) scope. It's starts from the inside and goes out.

EXAMPLE:

var jong = function(adam) {
  joe = adam * 2;
  var paul = function(j, a) {
    var kamui = aa * 2;
    console.log(j, kamui)
  }
  paul(joe, adam);
}

the inner scope of paul can access joe and adam. but joe and adam cant access
paul. If there are two variables with the same name; the inner one takes
priority.



3. Explain hoisting

Functions and variables are "hoisted" up during the compiling and are processed
first (of their scope). Declarations are hoisted, but assignments, even
assignments of function expressions, are not hoisted.


4. Describe function and variable hoisting

Both functions and variables are hoisted, which means they run first during the
compiling phase. Functions get hoisted first then the variables, then the rest
of the code.


5. Explain closure and common ways it’s used

Closure is when a function can access its lexical scope though it is not in the
scope. It's often used run functions inside a function as well as making modules

6. What makes closures so powerful?

Closures gives access to functions inside functions and allows the creation of
modules. This is very powerful in the case of constructors.  

7. Understand what modules are

Modules are functions that are enclosed in an outer scope; which then can be
invoked in various ways. 

8. What are two characteristics of modules?

1) an outer wrapping function being invoked, to create the enclosing scope
2) the return value of the wrapping function must include reference to at least
one inner function that then has closure over the private inner scope of the
wrapper.
