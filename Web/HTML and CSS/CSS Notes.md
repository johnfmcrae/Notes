# CSS Notes

Quick notes about CSS

## Units

- `em` element
- `rem` root element
- `vh` view height
- `vw` view width

## Undoing Things

You can undo a property of a specific element using `unset`.

```css
body {
    color: blue;
}

p {
    color: unset; /* unsets the blue text colour */
}
```

## IDs and Attributes

You can add an id in HTML,

```html
<div id="main"></div>
```

Then refer to that id in CSS with the `#` operator

```css
#main {
    /* styles */
}
```

You can also refer to an HTML attribute. For example, if we are using the `name` attribute in HTML,

```html
<input name="user-email" type="email"/>
```

we can refer to the name in CSS with square brackets,

```css
input[name="user-email"] {
    /* styles */
}
```

You can also exclude certain elements with the `:not` pseudo-class,

```css
.my-container p:not(.no-divider) {
    border-bottom: 1px solid #888989;
}
```

The above will add a border to all of the p elements in my-container that do not also have the no-divider class.

## Pseudo Elements and Classes

*Pseudo-elements* let you specify a specific subset of an element. For example, you may want to target the first element of a certain type. Pseudo-elements are specified with a double colon, `::`.

```css
.my-class::before {
    color: white;
}
```

You can also place the pseudo-elements in an element list,

```css
*, ::before, ::after {
  box-sizing: inherit;
}
```

*Pseudo-classes* define the behaviour for a special state of an element and are denoted with a single colon, `:`. For example, you can use the `:hover` pseudo-class to define mouse hover behaviour.

```css
button:hover {
  color: blue;
}
```

## Fallbacks

You can add **fallback** value which will be applied if the first value doesn't work in a particular browser. Fallbacks are often used when setting fonts, for example,

```css
body{
    font: -apple-system,Segoe UI,Roboto,Helvetica,Arial,sans-serif;
}
```

## Boxes, Containers, and So On

CSS has a shorthand for borders:

```css
element {
    border: <style> <colour> <width>;
}
```

Use the following to get CSS to take borders into account for sizing,

```css
 * {
  box-sizing: border-box;
}
```

## Screen Reader Only Styling

Add a description in an HTML `<span>` and style it with,

```css
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}
```
