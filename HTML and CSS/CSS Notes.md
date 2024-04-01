# CSS Notes

Quick notes about CSS

## Units

- `em` element
- `rem` root element
- `vh` view height
- `vw` view width

## The id Attribute

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

But using classes is more common.

## Fallbacks

You can add **fallback** value which will be applied if the first value doesn't work in a particular browser. Fallbacks are often used when setting fonts, for example,

```css
body{
    font: -apple-system,Segoe UI,Roboto,Helvetica,Arial,sans-serif;
}
```
