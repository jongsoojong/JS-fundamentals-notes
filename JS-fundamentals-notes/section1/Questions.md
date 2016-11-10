Types and Values


1. Name the primitive and object types in JS

There are 6 primitives and one object type in JS. The primitive are Number,
String, Boolean, Null, Undefined, and Symbol. The last one is Object(which
includes arrays)

2. Understand which types are stored by value and which are stored by reference

The scalar types are stored by value such as String, Boolean, Null, Undefined,
Number, Symbol. Compound values such as objects and arrays are stored by
reference.

3. Understand the difference between implicit and explicit type coercion

The real difference between implicit and explicit is whether or not the coercion
was done on purpose or by some side effect unknown to the user; so this can be
different to many people, HOWEVER; generally speaking explicit is when the
intent of coercion is obvious where as implicit is where the intent is not
obvious and the coercion happens as a side effect or due to rules in js.


4. What’s a common way to identify a type in JS?

Using the typeof operator is a great way to identify a type in js. Except for
null and NaN. Use isNaN for NaN.

5. Be able to explain the difference between == and ===

Simply put == allows type coercion and === does not.

6. Be able to give a couple of examples of both implicit and explicit coercion?

Examples of explicit coercion:
methods such as toString(), Number(), and Boolean().

Examples of implicit coercion:
like how if else statements change into boolean true and false. How 42 + ""
will change it to a string. The - operator changes things into numbers. 
