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
