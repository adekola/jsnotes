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

