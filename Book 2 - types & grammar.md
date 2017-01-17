#Chapter 1 - Types

> A type is an intrinsic, built-in set of characteristics that uniquely identifies the behavior of a particular value and distinguishes it from other values, both to the engine and to the developer.

###Built-in Types
JS has 7 built-in types

* `null`
* `undefined`
* `boolean`
* `number`
* `string`
* `object`
* `symbol` - new in ES6. 

With the exception of `object`, all of these types are called primitives.

When doing type checking with `typeof`, there's a gotcha to look out for - `typeof null === object;` returns `true`.

> `null` is the only primitive value that's "falsy" and as well returns "object" when type checked.

`typeof function(){}` would return `"function"`. While that seems like `function` is a high level built in type in JS, in reality it's actually a subtype of `object`. `function` is a special `object` in thta it is a callable `object`, which has an internal `[[Call]]` property that allows it to be invoked.

> That functions are in fact objects is a special feature in that they can have properties. for instance:

```
function a(b, c) {

}
a.length; // 2 - i.e. the number of params with which it was passed.
```

Arrays are `typeof`d as objects. They can however be thought of as subtypes of `object` with super powers of beign numerically indexed and not string keyed like plain or regular JS objects.

**In JS, variables have no types. Only Values. Variables can hold any value, at any time. **
You could think of that as JS doesn't do type enforcement i.e. insisting that a variable always hold the type of the value it starts with.

As such, `a = 42; typeof a;` is asking _what is the type of the value contained in a?_
> Note that `typeof` always returns a `string`.

**"undefined" vs undeclared**
An "undefined" variable exists in the accessible scope but has no value in it. an undeclared variable on the other hand doesn't exist (i.e. hasn't been formally declared) in the accessible scope. _This difference is significant_

> A ridiculous gotcha with `undefined` in JS - 

```
var a;

typeof a; // undefined
typeof b; // undefined

```

Although b is obviously undeclared, `typeof` indicates it's undefined. You should be aware of this gotcha. `undefined` may actually infer undeclared. Well, this is in fact a safety guard in that, `typeof` will not return a `ReferenceError` due to a variable being undeclared. Quite a handy feature.


#Chapter 2 - Values
##Arrays
Arrays are just containers which can hold heterogenous values. More-so, unlike other languages e.g C# and Java, you dont need to pre size your array in JS.

Arrays can have string keys/properties assigned to them, which do no count towards the length of the array.

