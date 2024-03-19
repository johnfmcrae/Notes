# JavaScript Basics

## Statements and Semicolons

Code statements are delineated by a semicolon in JavaScript, just like in many other languages.

```js
alert('Hello'); alert('World');

// same as
alert('Hello');
alert('World');
```

However, JavaScript can also perform **automatic semicolon insertion**.

```js
// also works
alert('Hello');
alert('World');
```

Automatic semicolons tend to work, but sometimes JavaScript gets it wrong, leading to nasty bugs. The community standard is therefore to **always use semicolons** in JavaScript.

## Using Modern JavaScript

To use the modern version of JavaScript, introduced in 2009, add the following to the top of the JavaScript file,

```js
"use strict";

// rest of the code...
```

Alternatively, you can add `"use strict"` to the beginning of a function, but most people apply the directive globally.

You need to specify `"use strict"` in the browser console also with,

```js
>> 'use strict'; <Shift+Enter for a newline>
//  ...your code
<Enter to run>
```

### Classes and Modules `use strict` Automatically

When writing simple code, feel free to throw in a `"use strict"` at the top of the file. In OOP code and things of the like, you don't need to.

[Contents](_main_javascript_notes.md)

## Variables

Use the `let` keyword to declare a variable in JavaScript. Features like varaible initialization and multi-varaible declaration are available.

```js
let animal;
animal = "monkey";

let fruit = "banana";

let firstName = "Herbie", lastName = "Hancock";
```

`let` is the modern variable declarator, but you may also come across the older `var` keyword in older scripts.

You always need to use the `let` keyword to declare a variable when you are within a `"use strict"` part of code. Older JavaScript supported implicit variable declaration.

```js
// no "use strict"
place = "Chicago"
```

But you shouldn't do this because as soon as you add a `"use strict"` you will get an error.

Camel case is the standard case convention for naming in JavaSctipt.

### Const

JavaScript also supports constants with the `const` keyword. Use capitalized names for global constants.

```js
const let SPEED_OF_LIGHT = 299792458;
```

## Types

There are eight data types in JavaScript

- Number
  - Includes both integer and floating point values
  - Also includes special numeric values such as `Infinity` and `NaN`
- BigInt
  - An integer of arbitrary length
  - Denoted by a trailing `n`, e.g. `bigInt = 123456789n;`
  - Not currently supported in Internet Explorer
- String
  - Can be denoted by single quotes ('), double quotes ("), or backticks (`).
  - Can embed variables with `${variable}` *if you are using backticks*
- Boolean
  - `true` or `false`
- `null`
  - does *not* mean a null reference
  - simply means "nothing", "empty", or  "unkown"
- `undefined`
  - used for the default initial value of a variable
- Symbol
  - for unique identifiers
- Objects

The `typeof` operator returns the type of a variable as a string. Beware that `typeof` has a bug where it reports the type of `null` as "object", which is incorrect but has been kept around for compatibility reasons.

### Conversion

For the most part, conversion works as you would expect. Here are a few notable cases and exceptions,

```js
Number(NaN)        // 0
Number(undefined)  // NaN
Boolean("abc")     // true
Boolean("0")       // true
Boolean(" ")       // true
Boolean("")        // false
Boolean(0)         // false
Boolean(null)      // false
Boolean(undefined) // false
Boolean(NaN)       // false
```

You can also use the plus sign `+` as a unary operator to do numeric conversion

```js
+""   // 0
+"3"  // 3
+true // 1
```

## Operators

JavaScript has all the good old operators. It also has,

- String concatenation with `+`
- Modify-in-place operators `+=` and `*=`
- Increment and decrement operators in both prefix and postfix form

## Conditionals, Loops, and So On

Conditionals, loops, breaks, switch cases, and the like work like they do in C.

JavaScript also has **arrow functions** which function like lambdas.
