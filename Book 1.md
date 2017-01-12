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
> `this` is not what you think it is. Coming from an OOP background, it's easy to expect `this` in JS to behave familiarly. Not so. If a > function has `this` reference within it,
> that usually points to an object. The particular object depends on how the function was called. `this` doesn't refer to the function itself.















