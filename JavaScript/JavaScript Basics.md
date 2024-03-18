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

Alternatively, you can add `"use strict";` to the beginning of a function, but most people apply the directive globally.

You need to specify `"use strict";` in the browser console also with,

```js
>> 'use strict'; <Shift+Enter for a newline>
//  ...your code
<Enter to run>
```

### Classes and Modules `use strict` Automatically

When writing simple code, feel free to throw in a `"use strict";` at the top of the file. In OOP code and things of the like, you don't need to.

[Contents](_main_javascript_notes.md)
