# jsnotes
Notes from my readings (and study) of YDKJS by @getify

Book 1: Up and Going
===================================

JS has **typed values** NOT typed variables. In other words, variables in and of themselves have no types. Only the values they hold have one of seven (as of ES6) 
types. The variables are only containers for the typed values.

_Interesting_
`typeof null` gives `"object"` instead of `"null"`. Watchout for such gotchas.

`undefined` is a value typeindicating the absence of a value. Hence, doing `var a = undefined` is entirely valid (although unintuitive). 
It is equvalent to an unassigned variable (i.e. a variable without a value) such as `var a;`

The `object` type is in fact a compound type which allows one to declare properties i.e. named locations that can each hold values of different types.

Arrays and functions should be thought of as specialized subtypes of the `object` type. Did you catch that? **Functions are `object`s in JS**. Never forget!!.

_Interesting_
Under the hood in JS, there are so-called Native object which wrap around primitive value types and are the basis for which you can call methods on such primitives.
For example:
```
var text = "Hello World";
var bill = 25.4635;

text.toUpperCase(); //HELLO WORLD
bil.toFixed(2); // 25.46
```
The `string` primitive is backed by a `String` objecj wrapper, a `number` primitive by a corresponding `Number` object. As required, JS auto boxes the primitive into the Native object type in order to access methods invoked.

**Truthy or Falsy Values**
_Falsy values_
* `""` - empty string
* `0`, `-0`, `NaN`
* `null`, `undefined`
* `false`

Any value not falsy as above is truthy.

**Attention - diff between `==` and `===`**
Contrary to the popular distinction made between the above 2 operators, the accurate difference is in the fact that `==` checks for value equality with coercion allowed (loose equality), while `===` checks for equality without coercion allowed. Hence, it's name as Strict equality operator.

Inequality operators in JS use coercion to do the relational comparison between values. i.e. **unlike the strict inequality operator**

`var` declares a variable which is at the current function scope or at the global scope if it is at the top level, outside of any function. _Hoisting_ is the metaphor 
for the idea that a `var` declaration is conceptually moved to the top of it's enclosing scope. and so is accessible throughout.

**Attention**
If you try to set a variable that hasn't been declared, you'll either end up creating a global variable or get an error if `stric mode` is on. Hence, **always formally declare your variables**
 
In ES6, `let` allows you to declare variables which are limited to specific blocks (i.e `{...}` pairs). It's called Block Scoping, unlike the `var` which enables function scoping.

> Strict Mode starting in ES5 allows you to restrict or enforce the rules on certain behaviors. Moreso, makes your code more optimizable for the engine.
You can opt in to `"use strict";`to strict mode at either the function or file level. One quick win with strict mode is that it doesnt't allow you
to set a variable which hasn't been declared.

**Thinking of functions as values**
Looking at this 
```
function fxn(){
  // do a few good stuff
}

```
What is not so obvious is that `fxn` is actually just a variable holding the function value that's being declared. In essence, functions are themselves values.

**Immediately Invoked Function Expressions (IIFE)**
```
(function IIFE(){
    console.log("I'll run right away, faster then Usain Bolt");
})();
// "I'll run right away, faster then Usain Bolt"

```

**Closures**

A closure can be thought of as a way to remember, and continue to access a function's scope even when the function is done running. 
The most common use of closures is in the **Module pattern** which entails creating a private implementation and exposing same via a public API.

**Attention** 

> `this` is not what you think it is. Coming from an OOP background, it's easy to expect `this` in JS to behave familiarly. Not so. it's dynamically bound based on how the function is executed. The particular object depends on how the function was called and not always or necessarily the function itself.

###Prototypes

If you reference a property on an object, if that property doesn't exist on the object, JS will automatically use that object's internal prototype refrence to find another object on which to locate the property. That prototype link is established at the time of object creation. Think in terms of an actual call to the `Object.create()` method.

> Do not abuse prototype linking by thinking of it as a sort of pseudo-class feature in JS. A more appropriate way to view it is as a means for "behavior delegation" -  a way to delegate from one object to another for needed behavior.

####Polyfill
[Polyfill](https://remysharp.com/2010/10/08/what-is-a-polyfill) is one means of accommodating holder browsers which have not yet implemented newer JS features. It involves taking a new feature and producing a piece of code which is equivalent and can run on older browsers. and It's best practise to use veted sets of polyfills such as [ES5-Shim](https://github.com/es-shims/es5-shim) as well as [ES6-Shim](https://github.com/es-shims/es6-shim) 

####Transpiling 
Transpiling (transforming + compiling) is the other option of supporting older browsers. It converts newer code into it's older equivalent. You'll typically insert the transpiler into your build process or as part of the linter for your minifier.

> In view of the pratical and important role of transpiler, consider unsing them as an integral part of your dev process. As the JS language continues to evolve, the ability to use new lang features while supporting older environments will be continue to be important.

[Babel](https://babeljs.io/) and [Traceur](https://github.com/google/traceur-compiler) are good transpiler options.

####Non-Javascript
As JS is written to be run in environments (browsers and servers), there'll be some part of JS code you'll write which use functions and objects that are not part of JS itself. For example, the DOM. `document` is a "host object", and the methods it exposes are but a thinly wrapped APi over built-in broswer implementations.
