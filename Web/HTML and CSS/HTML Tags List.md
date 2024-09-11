# HTML Tags List

Tags that you will use in HTML and how to use them

## Head and General

The bare-bones HTML boilerplate tags are,

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Page Title</title>
  </head>
</html>
```

Use the following to set the viewport,

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

## Body Elements

- `<section>`
- `<article>`
- `<footer>`
- `<a>` anchor element
- `<hr>` horizontal rule (self enclosing)

## A Note on Whitespace

Adding new lines does affect how the content is layed out. For example, if you have two `<p>` elements, each with their own class attributes,

```html
<p class="flavor">French Vanilla</p>
<p class="price">3.00</p>
```

and these classes are styled to be on the left and right hand side of their parent container,

```css
.flavor {
  text-align: left;
  width: 50%;
}

.price {
  text-align: right;
  width: 50%;
}
```

Then the new line will cause an extra space in the rendered page. If however, you place both `<p>` elements on the same line in the HTML file, then they will render on the same line,

```html
<p class="flavor">French Vanilla</p><p class="price">3.00</p>
```
