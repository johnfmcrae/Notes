# Objects

**Objects** in JavaScript are one of the eight data types supported by the language. Objects are not primitive; they can store data. JavaScript also has **classes**, which invoke a constructor and do other useful OOP things. In general then, you can think of JavaScript objects as a map/dictionary. JavaScript stores key-value pairs in objects, such as,

```js
let user = {
    name: "Steve", // note the comma
    age: 30,
    "Is a nice lad": true // note quotes for mulit-word keys
}; // note the semicolon
```

Keys are automatically converted to strings, so if for whatever reason, you decide to name a key a number, it will be cast to a string.

Empty objects can be initialized wither with the `new` keyword or with the **object literal** syntax,

```js
let user = new Object();
let user = {};
```

## Accessing Object Properties

Object properties are accessed using a period and are deleted with the `delete` operator,

```js
alert( user.name ); // Steve
alert( user.age );  // 30
delete user.age;
alert( user.age ); // undefined
```

Once an object has been created, you can dynamically add properties to it.

```js
user.isVlaid = true;
alert( user.isValid ); // true
```

You can also access properties using square brackets,

```js
alert( user["Is a nice lad"] ); // true
```

Doing so allows you to access a key using a variable,

```js
let key = "name"
alert( user[key] ); // "Steve"
```

## Computed Properties

Using square brackets in an object makes that property a **computed property**. For example,

```js
let fruit = prompt("Which fruit to buy?", "apple");

let bag = {
    [fruit]: 5
};

alert( bag.apple ); // 5 (assuming user choose "apple" as the prompt)
```

You can also do things like string concatenation in computed properties.

```js
let fruit = prompt("Which fruit to buy?", "apple");

let bag = {
    [fruit + 'Number']: 5
};

alert( bag.appleNumber ); // 5 (assuming user choose "apple" as the prompt)
```

## Property Value Shorthand

JavaScript supports using a value when assigning a property.

```js
function makeUser(name, age) {
    return {
        name: name,
        age: age,
    }
}
```

This is actually very common, so much so that JavaScript has a special shorthand for it called **property value shorthand**,

```js
function makeUser(name, age) {
    return {
        name,
        age,
    }
}
```

## The `in` and `for..in` Operators

JavaScript has the `in` operator which returns a true if a key is not `undefined` in an object.

```js
let user = { name: "Karl", age: 30};

alert( "age" in user );    // true
alert( "hummus" in user ); // false

let key = "age";

alert( key in user ); // true
```

JavaScript also supports range based looping with the `for..in` operator,

```js
let user = {
  name: "Jeff",
  age: 30,
  isAdmin: true
};

for (let key in user) {
  alert( key );  // name, age, isAdmin
  alert( user[key] ); // Jeff, 30, true
}
```

## Object Order

Properties in an object are ordered by creation, unless the keys are integers.

```js
let codes = {
  "49": "Germany",
  "41": "Switzerland",
  "44": "Great Britain",
  // ..,
  "1": "USA"
};

for (let code in codes) {
  alert(code); // 1, 41, 44, 49
}
```

If you want to maintain creation order, you can use the string concatenation operator, `+`.

```js
let codes = {
  "+49": "Germany",
  "+41": "Switzerland",
  "+44": "Great Britain",
  // ..,
  "+1": "USA"
};

for (let code in codes) {
  alert( +code ); // 49, 41, 44, 1
}
```

[Contents](_main_javascript_notes.md)
