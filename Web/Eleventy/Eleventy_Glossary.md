# Eleventy Glossary

## Front Matter

You can add front matter in YAML to your Markdown content to specify things like lage title, layout, and even some common page attributes like page summaries and subheadings.

For example,

```yaml
---
title: 'Hello, world'
layout: 'layouts/home.html'
intro:
  eyebrow: 'Digital Marketing is our'
  main: 'Bread & Butter'
  summary: 'Let us help you create the perfect campaign with our multi-faceted team of talented creatives.'
  buttonText: 'See our work'
  buttonUrl: '/work'
  image: '/images/bg/toast.jpg'
  imageAlt: 'Buttered toasted white bread'
---
```

## Passthrough

Use passthroughs to send files that are not Eleventy templates to the output. You will commonly use this to pass images to pages.

Add passthroughs to the `.eleventy.js` file,

```js
module.exports = config => {
    config.addPassthroughCopy('./src/images/'); // here is some passthrough
    return {
        markdownTemplateEngine: 'njk',
        dataTemplateEngine: 'njk',
        htmlTemplateEngine: 'njk',
        dir: {
            input: 'src',
            output: 'dist'
        }
    };
};
```

## Partials

Partials are reusable bits of Eleventy code which you can use to, for example, insert a consistent header across your website. You can include a short HTML file in an Eleventy file using Nunjucks with the `{% include <file> %}` syntax.
