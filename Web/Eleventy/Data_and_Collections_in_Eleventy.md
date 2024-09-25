# Data and Collections in Eleventy

You can easily access data from JSON files in Eleventy. Let's say you have a JSON file called `navigation.json` with a list of elements for you site navigation,

```json
{
  "items": [
    {
      "text": "Home",
      "url": "/"
    },
    {
      "text": "About",
      "url": "/about-us/"
    },
    {
      "text": "Blog",
      "url": "/blog/"
    },
    {
      "text": "Contact",
      "url": "/contact/"
    }
  ]
}
```

You can add these elements to site header partial with,

```html
<ul class="nav__list">
  {% for item in navigation.items %}
  <li>
    <a href="{{ item.url }}">{{ item.text }}</a>
  </li>
  {% endfor %}
</ul>
```

Notice the JavScript syntax in the curly brackets. We are accessing the navigation data here by referring to its filename, `navigation.json`.

## Defining Your Own Collections

You can define a collection in your main `eleventy.js` file and refer to it as you would data in other places.
