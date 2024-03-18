# The JavaScript Language

JavaScript is a scripting language that traditionally runs in web browsers. These days, it can also run in servers that have the JavaScript engine.In fact, web browswers actually run JavaScript by using an embedded Javascript engine sometimes referred to as a *JavaScript virtual machine*.

A few engines to know:

- V8 in Chrome, Opera, and Edge
- SpiderMoney in Firefox
- SquirrelFish in Safari
  
## In-Browser JavaScript

JavScript that runs in a browser environment (as opposed to say, in Node.js on a server), is meant to be isolated to that web browser.

It can:

- Add HTML to a page
- Modify page styles
- Respond to user events
- Get and set cookies

It cannot:

- Read or write arbitrary files on disk (unless initiated by a user action such as "dropping" a file)
- Know about things happening in separate tabs or windows (unless you explicitly set up communication between two pages)
- Receive data from other sites or domains outside of the current page (again, unless explicitly set up)

## Calling JavaScript in a Browser

You can call JavaScript from an HTML page using the `<script>` tag,

```html
<html lang="en">
    <body>    
    <p>Before the script...</p>

    <script>
        alert( 'Hello from JS!');
    </script>

    <p>... after the script.</p>
    </body>
</html>
```

You can also point to a JavaScript file or a URL,

```html
<script src="path/to/scriptFromFile.js"></script>
<script src="https://website.web/scriptFromURL.js"></script>
```

Note that if `src` is set, the script content gets ignored

```html
<script src="someFile.js">
    alert( 'Hello from JS!'); // this content is ignored
</script>
```
