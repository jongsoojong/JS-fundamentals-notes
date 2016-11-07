You Don't Know JS: Types & Grammar Notes:

Chapter 2: Values:


Arrays:
--------------------------------------------------------------------------------

An array can contain many different values: from strings to numbers to even
arrays. Arrays can also create 'sparse' which are empty positions in arrays.
We will try to avoid this.

//Example:
a[0] = 1;
a[2] = "jong";

a[1] is a sparse and is undefined.
//


Arrays can also have string properties *did not know that*.
However generally this is not normally used, people use objects for key value
pairs.

So array['jong'] = jong; works...

//Fun Fact:
If you write a number with quotes as in a string it will coerce into a number
value.

a['13']

a.length = 14.
//


Array-likes:
--------------------------------------------------------------------------------

You can often convert array-like stuff such as collection of values into an
array, using array utilities(indexOf, concat, forEach).

//Example:
function foo() {
    var arr = Array.prototype.slice.call( arguments ); *what is this call*
    arr.push( "bam" );
    console.log( arr );
}

foo( "bar", "baz" ); // ["bar","baz","bam"]
//

ES6 has its own called Array.from();


Strings:
--------------------------------------------------------------------------------

Strings and Chars share many similarities; however there are numerous
differences too.

JavaScript strings are immutable, while arrays are quite mutable A further
consequence of immutable strings is that none of the string methods that alter
its contents can modify in-place, but rather must create and return new strings.

//Example:
c = a.toUpperCase();
a === c;    *false*
a;          *"foo"*
c;          *"FOO"*
//

Therefore sometimes it is useful to turn strings into a collection of chars in
arrays. This is useful for using certain array methods that does not exist in
strings. Examples include .split, .join.



Numbers:
--------------------------------------------------------------------------------

JavaScript has just one numeric type: number. This type includes both "integer"
values and fractional decimal numbers. In JS a integer is any number thats not
a fraction or decimal.

Small tidbits about numbers and decimals:

* leading decimal 0s and 0's following a decimal can be cut (provided there is
  nothing after the 0) EX: 0.42 can be written as .42 and 43.0 can be written as
  43., though 43. is not commonly used.

* Trailing 0's after a decimal will be removed.

* Very large or very small numbers will come out as exponents "5E10"

* Numbers have many methods such as toFixed(*total number of decimals*),
toPrecision(*total number of digits*). Also since it takes it literally you have
to either cover the numbers with () if it doesnt have a decimal in the number.


Small decimal values:  

* Simply put, 0.3 + 0.2 === 0.5 is actually false the reason being that 0.3 is
actually not really 0.3 but a very close number to 0.3

*  ES6 has Number.EPSILON to help solve this problem

Testing for integers:

* For ES6 we use .isInteger


Special Values:
--------------------------------------------------------------------------------


Null and Undefined:

* For null and undefined, they are both its type and its value.

* Null is an empty value while undefined is a missing value. OR! Null had a
value and doesn't anymore and undefined hasn't had a value yet.

* Null is a SPECIAL keyword and not an identifier, undefined is.

* NEVER OVERRIDE undefined.

Void Operator:

* Void nullified any value and makes it undefined

* This doesn't modify the existing value; just ensures that no value comes back.


Special Numbers:
--------------------------------------------------------------------------------


Not A Number(NaN):

*  NaN stands for 'Not a Number' but thats not very accurate, its more like
invalid number, failed number  or bad number', therefore NaN is a number.

* NaN cannot == or === itself; it will come back as false. however we can use
isNaN to do that job.


Infinity:

* Infinity becomes the result when either the number becomes too high (2 to the
  power of 970), or you divide by zero or something that creates infinity.

//Fun Fact:

Infinity / Infinity is not a defined operation. In JS, this results in NaN.

But what about any positive finite number divided by Infinity? 0.

//


Zeros:

* JS has 3 different zeroes. 0, positive zero, and negative zero.

* Why would we need a negative zero. Example : if a variable arrives at zero and
it loses its sign, then you would lose the information of what direction it was
moving in before it arrived at zero. Preserving the sign of the zero prevents
potentially unwanted information loss.




Value vs Reference:
--------------------------------------------------------------------------------

Simple values (aka scalar primitives) are always assigned/passed by value-copy:
null, undefined, string, number, boolean, and ES6's symbol.

//Example:

a = 3
b = a;
b++;
console.log(a + ' ' + b) *3 4*
//

Compound values -- objects (including arrays) and functions always create a copy
of the reference on assignment or passing.

//Example:
var jongArray = [1,2,3];
var jongSooArray = jongArray;

jongSooArray.push(4);

console.log(jongArray); *[1,2,3,4]*
//

So how can we change stuff by reference? If its an array we can copy it by using
slice.

And how can we change values to change via reference? We use a wrapper to make
it so.
