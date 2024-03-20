# Code Quality

## Debugging

You can debug javascript in most web browsers. There you should find a debugger tab, a console tab, and a bunch of other handy tabs.

JavaScript also has a few commands and functions to help with debugging, namely, `debugger` and `console.log()`

```js
// some code

debugger; // causes a breakpoint

// open console to see
for (let i = 0; i < 5; i++) {
  console.log("value,", i);
}
```

The `debugger` command creates a breakpoint in the code *only when the developer tools are open*.

[Contents](_main_javascript_notes.md)

## Transpilers and Polyfills

**Transpilers** and **polyfills** are tools which help us to write modern JavaScript while maintaining backwards compatibility with older browsers.

**Transpilers** replace new syntax with older equivalents, for example,

```js
// before running the transpiler
height = height ?? 100;

// after running the transpiler
height = (height !== undefined && height !== null) ? height : 100;
```

**Polyfills** implement new functions, for example,

```js
if (!Math.trunc) { // if no such function
  // implement it
  Math.trunc = function(number) {
    // Math.ceil and Math.floor exist even in ancient JavaScript engines
    // they are covered later in the tutorial
    return number < 0 ? Math.ceil(number) : Math.floor(number);
  };
}
```

[Contents](_main_javascript_notes.md)
