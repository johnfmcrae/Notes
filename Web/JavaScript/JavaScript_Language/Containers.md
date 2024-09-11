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

You can therefore use arrays as either a stack or a queue.

Be advised that manipulating an array as a stack using the `push` and `pop` metods is more performant than moving the whole array around with the `shift` and `unshoft` methods.

### Looping Over Arrays

Recall the `for..in` syntax from [objects](Objects.md),

```js
let fruits = ["Apple", "Orange", "Pear"];

for (let key in fruits) {
  alert( fruits[key] );
}
```

This is convenient if you need to use the keys in your loop. If not, the `for..of` syntax is a cleaner option,

```js
let fruits = ["Apple", "Orange", "Plum"];

for (let fruit of fruits) {
  alert( fruit );
}
```

Furthermore, `for..of` is optimized for looping over arrays and the `for..in` loop will access *all* of the properties of your array, which risks leading to nasty bugs. In general, stick with `for..of` for arrays.

[Contents](_main_javascript_notes.md)
