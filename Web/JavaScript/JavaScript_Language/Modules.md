# JavaScript Modules

A JavaScript **module** is a JavaScript file. Modules typically contain a class or a library containing a collection of functions.

## Importing and Exporting

You use modules with the `import` and `export` keywords. `export` is what you use in a file to indicate what you want to be made available elsewhere and `import` is how you get that code into a different file.

Say we have a file called **addTwo.js** that includes a simple function,

```js
function addTwo(a, b) {
	console.log(a + b);
}
```

There are many ways to make the above function into a module. Two common methods are to use,

- Default exports
- Named exports

### Default Exports

You can have only one default export per JavaScript file. To make the addTwo function a module using a default export you can do either of the following,

```js
export default function addTwo(a, b) {
	console.log(a + b);
}

// or

function addTwo(a, b) {
	console.log(a + b);
}

export default addTwo;
```

### Named Exports

Named exports allow you to export certain parts of a JavaScript file. You can use both default and named exports in the same file. Again, there are multiple ways to export,

```js
export function addTwo(a, b) {
	console.log(a + b);
}

export function addThree(a, b, c) {
	console.log(a + b + c); 
}

// or

function addTwo(a, b) {
	console.log(a + b);
}

function addThree(a, b, c) {
	console.log(a + b + c); 
}

export { addTwo, addThree };
```

### Imports

Use the `import` keyword to import a module. Named exports require curly braces and default exports do not. You can also name a variable imported from a default export whatever you want.

```js
// named export
import { addTwo } from "./addTwo";

// default export
import addTwo from "./addTwo";
// also works
import addThemUp from "./addTwo";
```