# React Basics

React is a JavaScript library, which along with ReactDOM, forms a popular frontend framework for web development.

React uses **JSK** markup syntax. Here's an example,

```js
function AboutPage() {
  return (
    <>
      <h1>About</h1>
      <p>Hello there.<br />How do you do?</p>
    </>
  );
}
```

## React Terminology

### Component

A reusable piece of code that represents a part of a user interface.

Components must start with capital letters. When using components, thing of defining a component as a JavaScript function and calling it as a HTML tag.

```js
function Square({ value }) {
  return <button className="square">{value}</button>;
}

export default function Board() {
  return (
    <>
      <div className="board-row">
        <Square value="1" />
        <Square value="2" />
        <Square value="3" />
      </div>
    </>
  );
}
```

### Element

A combination of JavaScript code and HTML tags that describe what to display.

### Fragment

A grouping of multiple elements.

## Events

Certain DOM elements have their own event triggers which React recognizes. For example, the HTML `<button>` element has an `onClick` attribute. When defining your own components, you can call the events what you want, but the convention is to use *on* as a prefix. So maybe you have a `helpButton` component, you would then want to give it a `onHelpButtonClick` event name.

Similarly, event handlers typically start with a *handle* prefix. So in our example, the handler would be called `handleHelpButtonClick`.
