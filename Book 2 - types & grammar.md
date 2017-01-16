##Types

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


