You Don't Know JS: this & Object Prototypes

Chapter 5: Prototypes



Notes:
--------------------------------------------------------------------------------


* If the property name foo ends up both on myObject itself and at a higher level
of the [[Prototype]] chain that starts at myObject, this is called shadowing.
The foo property directly on myObject shadows any foo property which appears
higher in the chain, because the myObject.foo look-up would always find the foo
property that's lowest in the chain.
