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

You an add an id in HTML,

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

## Fallbacks

You can add **fallback** value which will be applied if the first value doesn't work in a particular browser. Fallbacks are often used when setting fonts, for example,

```css
body{
    font: -apple-system,Segoe UI,Roboto,Helvetica,Arial,sans-serif;
}
```
