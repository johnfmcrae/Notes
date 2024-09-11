# JavaScript Classes

In JavaScripts, classes are a special kind of function which contain a `constructor`.

```js
class User {
    constructor(name) { this.name = name; }
    sayHi() { alert(this.name); }
}

alert(typeof User); // function
```