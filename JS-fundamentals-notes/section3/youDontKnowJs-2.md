You Don't Know JS: this & Object Prototypes

Chapter 2: this All Makes Sense Now!:



Call-Site:
--------------------------------------------------------------------------------

*  Call-site: the location in code where a function is called (not where it's
declared)

* Call-stack (the stack of functions that have been called to get us to the
current moment in execution). The call-site we care about is in the invocation
before the currently executing function.



Random notes about binding:
--------------------------------------------------------------------------------

* The first rule (of 4) we will examine comes from the most common case of
function calls: standalone function invocation. Think of this this rule as the
default catch-all rule when none of the other rules apply.

* Usually binds to global when its out in the global scope, ow do we know that
the default binding rule applies here? We examine the call-site

* The way Default-binding works might change depending on strict or non-strict
mode.

* One of the most common frustrations that this binding creates is when an
implicitly bound function loses that binding, which usually means it falls back
to the default binding, of either the global object or undefined, depending on
strict mode.

* Explicit binding usually uses the methods .call() and .apply();

* bind(..) returns a new function that is hard-coded to call the original
function with the this context set as you specified.

* If you pass a simple primitive value (of type string, boolean, or number)
as the this binding, the primitive value is wrapped in its object-form (
new String(..), new Boolean(..), or new Number(..), respectively). This is
often referred to as "boxing".

* When a function is invoked with new in front of it, otherwise known as a
constructor call, the following things are done automatically:

-a brand new object is created (aka, constructed) out of thin air
-the newly constructed object is [[Prototype]]-linked
-the newly constructed object is set as the this binding for that function call
-unless the function returns its own alternate object, the new-invoked function
call will automatically return the newly constructed object.

* Explicit binding takes precedence over implicit binding, which means you
should ask first if explicit binding applies before checking for implicit
binding.

RULES: On how This applies
--------------------------------------------------------------------------------

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

var bar = foo()

exception:

1. If you pass null or undefined as a this binding parameter to call, apply, or
 bind, those values are effectively ignored, and instead the default binding
 rule applies to the invocation.


* Instead of the four standard binding rules, ES6 arrow-functions use lexical
scoping for this binding, which means they adopt the this binding (whatever it 
is) from its enclosing function call. They are essentially a syntactic
replacement of self = this in pre-ES6 coding.
