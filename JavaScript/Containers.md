# JavaScript Containers

In addition to objects, which store data in keyed collections, JavaScript also has many of the classic collections that you would expect.

## Arrays

Arrays are denoted with square brackets in JavaScript. You can initialize an array with empty brackets or with the `new` operator,

```js
let array1 = [];
let array2 = new Array()
```

Array indices are zero-based (no MATLAB-style nonsense here) and behave as you would expect

```js
let fruits = ["Apple", "Orange", "Plum"];
alert( fruits[0] ); // "Apple"
alert( fruits[3] ); // undefined
fruits[3] = "Lemon"; // dynamic allocation
alert( fruits[3] ); // "Lemon"
```

You can also do Python-style negative indexing using the `at` method. Be advised that this is a newer feature in JavaSctipt,

```js
let fruits = ["Apple", "Orange", "Plum"];
alert( fruits[0] ); // "Apple"
alert( fruits.at(-1) ); // "Plum"
```

Array length is accessible with the `.length` *property*. Note that `.length` is a property and therefore does not need any brackets.

```js
let fruits = ["Apple", "Orange", "Plum"];
alert( fruits.length ); // 3
```

### Operations on Arrays

JavaScript supports the following add and access operations:

- `push` adds an item to the end of the array
- `pop` returns and removes the last item from the array
- `shift` returns and removes the first item in the array
- `unshift` adds an item to the beginning of the array

You can therefore use arrays as either a stack or a queue.s

[Contents](_main_javascript_notes.md)
