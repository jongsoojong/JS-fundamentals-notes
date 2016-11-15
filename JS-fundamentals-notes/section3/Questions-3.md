1. Be able to explain what the keyword ‘this’ represents



2. What is the call site?

the location in code where a function is called (not where it's declared)


3. How can we explicitly alter what ‘this’ represents?

By using call or apply.

4. How can we implicitly alter what ‘this’ represents?




5. What are the four rules for determining what ‘this’ is?

1. Is the function called with new (new binding)? If so, this is the newly
constructed object.

var bar = new foo()

2. Is the function called with call or apply (explicit binding), even hidden
inside a bind hard binding? If so, this is the explicitly specified object.

var bar = foo.call( obj2 )

3. Is the function called with a context (implicit binding), otherwise known as
an owning or containing object? If so, this is that context object.

var bar = obj1.foo()

4. Otherwise, default the this (default binding). If in strict mode, pick
undefined, otherwise pick the global object.
--------------------------------------------------------------------------------
Understand what object prototypes are

1. How do objects share or inherit properties?

They create a link between the objects where one object delegates functions
and property to another.

2. What is behavior delegation?

Behavior delegation is where if an object does not have the property or method
needed it will delegate to another object for those property and methods.

3. Understand property shadowing

Shadowing is when there are two property names that are the same on two
different places on the prototype chain. Usually the property on the lower
level of the chain is called because the look up is from the bottom up. However
depending on strict-ness of the code different things happen.

1. If a normal data accessor (see Chapter 3) property named foo is found anywhere
higher on the [[Prototype]] chain, and it's not marked as read-only (writable:
false) then a new property called foo is added directly to myObject, resulting
in a shadowed property.

2. If a foo is found higher on the [[Prototype]] chain, but it's marked as
read-only (writable:false), then both the setting of that existing property as
well as the creation of the shadowed property on myObject are disallowed. If the
code is running in strict mode, an error will be thrown. Otherwise, the setting
of the property value will silently be ignored. Either way, no shadowing occurs.

3. If a foo is found higher on the [[Prototype]] chain and it's a setter
(see Chapter 3), then the setter will always be called. No foo will be added to
(aka, shadowed on) myObject, nor will the foo setter be redefined.


4. Know the difference between Classical and Prototypal Inheritance

Classical inheritance normally copies the traits, however js uses Prototypal
inheritance which is for more dynamic-language version of classical. In essence
they are very different as Prototypal Inheritance does not copy but rather
links the objects together and delegates their traits.

6. Be familiar with the pseudoclassical instantiation style

Here it is.
//
var Func = function() {
  this.a = 0;
  this.b = 1;
}

Func.prototype.method1 = function() {
  // code for method1 here...
}

Func.prototype.method2 = function() {
  // code for method2 here...
}

Func.prototype.logA = function() {
  return this.a;
}

var myFunc = new Func();
myFunc.logA(); // returns a
//

7. Understand the ‘OLOO’ pattern and how it makes inheritance intuitive

OLOO stands for Objects-Linked-to-Other-Objects. It is intuitive because instead
of parent and child inheritance it delegate each other as a peer. Think
horizontally and not vertically.

8. Know common methods and keywords like ‘new’ and Object.create()

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object
