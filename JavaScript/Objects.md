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

## Objects and References

In JavaScript, primitives are always stored **by value** and objects are always stored **by reference**.

Consequently, assignment operations on objects always copy the reference and do not duplicate the value in memory.

```js
let user = { name: "Jack" };
let admin = user; // admin points to the same value in memory as user
```

In a sense, you can think of objects like you would pointers in C. With that in mind, consider the following,

```js
let a = {};
let b = a; // b points to the same address as a

alert( a == b && a === b); // both true

let c = {}; // c points to some address
let d = {}; // d points to some other address
alert( c == d ); // false, addresses are not the same
```

In order for object comparison to return a `true`, the objects being compared must be the same.

You can copy the value of an object using the `Object.assign(destination, ...sources)` function.

```js
let user = { name: "John" };

let permissions1 = { canView: true };
let permissions2 = { canEdit: true };

// copies all properties from permissions1 and permissions2 into user
Object.assign(user, permissions1, permissions2);

// now user = { name: "John", canView: true, canEdit: true }
alert(user.name); // John
alert(user.canView); // true
alert(user.canEdit); // true
```

Leaving the `destination` parameter empty lets you perform a clone of an object,

```js
let user = {
  name: "John",
  age: 30
};

let clone = Object.assign({}, user);

alert(clone.name); // John
alert(clone.age); // 30
```

### Deep Clones

Cloning an object that has a nested object will copy a reference to the nested object, as opposed to cloning that object also.

```js
let user = {
  name: "John",
  sizes: {
    height: 182,
    width: 50
  }
};

let clone = Object.assign({}, user);

alert( user.sizes === clone.sizes ); // true, same object

// user and clone share sizes
user.sizes.width = 60;    // change a property from one place
alert(clone.sizes.width); // 60, get the result from the other one
```

To perform a **depp clone**, use the `structuredClone` method.

```js
let user = {
  name: "John",
  sizes: {
    height: 182,
    width: 50
  }
};

let clone = structuredClone(user);

alert( user.sizes === clone.sizes ); // false, different objects

// user and clone are totally unrelated now
user.sizes.width = 60;    // change a property from one place
alert(clone.sizes.width); // 50, not related
```

[Contents](_main_javascript_notes.md)
