You Don't Know JS: Types & Grammar Notes:

Chapter 4: Coercion:

The Ultra-Layman's terms of coercion is when one type becomes another type
due to explicit or implicit reasons.

"explicit coercion" is when it is obvious from looking at the code that a type
conversion is intentionally occurring, whereas "implicit coercion" is when the
type conversion will occur as a less obvious side effect of some other
intentional operation.

//Example:
var a = 42;

var b = a + "";         // implicit coercion

var c = String( a );    // explicit coercion
//

Some facts right off the bat. Only scalar primitives will coerce. Functions
and Objects are usually not the results of Coercion.


*EXPLICIT*


To String:
-------------------------------------------------------------------------------

* We use the toString to change types into strings.

* Built-in primitive values have natural stringification: null becomes "null",
undefined becomes "undefined" and true becomes "true".

* If you toString an Array you get the values in the array separated by commas.

* JSON stringification is similar to toString but has some subtle differences.

* String, number, boolean, and null values all stringify for JSON basically
the same as how they coerce to string values via the rules of the ToString
abstract operation.

* If you pass an object value to JSON.stringify(..), and that object has a
toJSON() method on it, toJSON() is automatically called to (sort of) "coerce"
the value to be JSON-safe before stringification.


To Number:
--------------------------------------------------------------------------------

* normally turns strings with numbers in them into just numbers, but also does
these interesting things : true becomes 1 and false becomes 0. undefined becomes
NaN, but (curiously) null becomes 0.

* Objects (and arrays) will first be converted to their primitive value
equivalent, and the resulting value (if a primitive but not already a number) is
coerced to a number according to the ToNumber rules just mentioned.

//Example:

var a = {
    valueOf: function(){
        return "42";
    }
};

var b = {
    toString: function(){
        return "42";
    }
};

var c = [4,2];
c.toString = function(){
    return this.join( "" ); // "42"
};

Number( a );            // 42
Number( b );            // 42
Number( c );            // 42
Number( "" );           // 0
Number( [] );           // 0
Number( [ "abc" ] );    // NaN

//



To Boolean:
--------------------------------------------------------------------------------

* Booleans results in true and false. They can also be coerced into numbers via
0 and 1. However thats not all: We have truthy and falsy values.

* All of JavaScript's values can be divided into two categories:
 -values that will become false if coerced to boolean
 -everything else (which will obviously become true)

* These are the falsy values that will become false if you coerce them into a
boolean. Everything else is truthy.

undefined
null
false
+0, -0, and NaN
""

* Falsy values can be finicky and confusing; Just re-read the section if you
need to brush up.

//Fun Facts:
ParseInt gets rid of the characters in a string with numbers. Does not coerce
though. Also always pass in a STRING though ParseInt

The unary ! negate operator explicitly coerces a value to a boolean. The problem
is that it also flips the value from truthy to falsy or vice versa. So, the most
common way JS developers explicitly coerce to boolean is to use the !!
double-negate operator, because the second ! will flip the parity back to the
original
//


Implicit
--------------------------------------------------------------------------------

* Implicit coercion refers to type conversions that are hidden, with non-obvious
side-effects that implicitly occur from other actions. In other words, implicit
coercions are any type conversions that aren't obvious (to you).

Here are some odd implicit rules you might run into:

*  if either operand to + is a string (or becomes one with the above steps!),
the operation will be string concatenation. Otherwise, it's always numeric
addition.

* You can coerce a number to a string simply by "adding" the number and the ""
empty string.

*  The - operator is defined only for numeric subtraction, so a - 0 forces a's
value to be coerced to a number. While far less common, a * 1 or a / 1 would
accomplish the same result, as those operators are also only defined for numeric
operations.

* The stuff that forces a boolean implicit coercion:
   - The test expression in an if (..) statement.
   - The test expression (second clause) in a for ( .. ; .. ; .. ) header.
   - The test expression in while (..) and do..while(..) loops.
   - The test expression (first clause) in ? : ternary expressions.
   - The left-hand operand (which serves as a test expression -- see below!)
   to the || ("logical or") and && ("logical and") operators.


Loose equality vs Strict equality:
--------------------------------------------------------------------------------

* == allows coercion in the equality comparison and === disallows coercion.
If you want coercion, use == loose equality, but if you don't want coercion, use
 === strict equality.

* Read the implicit coercion part; there is a ton of edge cases and other
interesting things.

* TL:DR :

Explicit coercion is code which is obvious that the intent is to convert a value
from one type to another. The benefit is improvement in readability and
maintainability of code by reducing confusion.

Implicit coercion is coercion that is "hidden" as a side-effect of some other
operation, where it's not as obvious that the type conversion will occur. While
it may seem that implicit coercion is the opposite of explicit and is thus bad
(and indeed, many think so!), actually implicit coercion is also about improving
the readability of code.

Especially for implicit, coercion must be used responsibly and consciously. Know
why you're writing the code you're writing, and how it works. Strive to write
code that others will easily be able to learn from and understand as well.
