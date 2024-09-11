# Eleventy Quick Start

This note summarizes the steps that the [Learn Eleventy From Scratch](https://learneleventyfromscratch.com/) tutorial takes to get an Eleventy page up and running.

## 1. Create Your Root Folder, Source Files, and .gitignore File

- Create your top level directory
- Make your source file directory and if you have anything, add any content.
- Make a gitignore and add the following,

```bash
# Misc
*.log
npm-debug.*
*.scssc
*.swp
.DS_Store
Thumbs.db
.sass-cache
.env
.cache

# Node modules and output
node_modules
dist
src/_includes/css
```

## 2. Create the Basic Eleventy File

- Make a new file called `.eleventy.js` and add the following,

```js
module.exports = config => {
  return {
    dir: {
      input: 'src',
      output: 'dist'
    }
  };
};
```

- In the terminal, in your top-level directory, run the following, which will create a `package.json` file,

```bash
npm init -y
```

- Next, run the following to install a local version of Eleventy,

```bash
npm install @11ty/eleventy
```

- Modify the script to include the "start" line, so that the `package.json` file looks like this,

```js
{
  "name": "eleventy-from-scratch",
  "version": "1.0.0",
  "description": "",
  "main": ".eleventy.js",
  "scripts": {
    "start": "npx eleventy --serve"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "@11ty/eleventy": "^0.11.0"
  }
}
```

- You can now add an `index.md` file in your source directory to try out a page
- To render the page, run,

```bash
npm start
```
