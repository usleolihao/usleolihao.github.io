# Docsify 

# [![logo](https://docsify.js.org/_media/icon.svg)](https://docsify.js.org) <!-- {docsify-ignore} -->

## Quick start 

### installation

```bash
npm i docsify-cli -g
```

### Initialize

./docs is the path that us for the documentation.

```bash
dosify init ./docs
```

### writing content

* `index.html` as the entry file
* `README.md` as the home page
* `.nojekyll` prevents GitHub Pages from ignoring files that begin with an underscore

!> We need put the `.nojekyll`  in root directory, if the directory structure is as follows:
```text
.
├── index.hmtl
├── README.md
├── .nojekyll
└── docs
    ├── README.md
    ├── guide.md
    └── zh-cn
        ├── README.md
        └── guide.md
└── docs2
    ├── README.md
    ├── guide.md
    └── zh-cn
        ├── README.md
        └── guide.md
```

### Preview the site

You can replace `docs` with the root path `.` if you have the above directory structure. (It means your site is not just docsify, and you may build your site with HTML, js, or asp.)

```bash
docsify serve docs
```

You can preview your site in your browser on `http://localhost:3000.`

## Writing More pages

### More pages and routes
```text
.
└── docs                    
    ├── README.md           => http://domain.com
    ├── guide.md            => http://domain.com/#/guide
    └── zh-cn
        ├── README.md       => http://domain.com/#/zh-cn/
        └── guide.md        => http://domain.com/#/zh-cn/guide

```

### Sidebar

need to set `loadSidebar` to **true**
```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```
Create the `_sidebar.md`:

```markdown
<!-- docs/_sidebar.md -->

* [Home](/)
* [Guide](guide.md)
```

!> Create a .nojekyll in ./docs to prevent GitHub Pages from ignoring files that begin with an underscore.

```bash
touch .nojekyll
```
!> For Github Pages, you need place `.nojekyll` in root path.

```text
└── docs/
    ├── _sidebar.md
    ├── index.md
    ├── getting-started.md
```

### Nested Sidebar

`_sidebar.md` only navigation to reflect the current directory by adding a `_sidebar.md` file to each folder.

```text
.
└── docs                    
    ├── README.md              => use it as the landing page for the route.
    ├── guide.md
    ├── _sidebar.md            => http://domain.com 
    └── zh-cn
        ├── README.md          => use it as the landing page for the route.
        └── guide.md
        └── _sidebar.md         => http://domain.com/#/zh-cn/
```

`_sidebar.md` is loaded from each level directory. If the current directory doesn't have `_sidebar.md`, it will fall back to the parent directory.
```text
.
└── docs                    
    ├── README.md              => use it as the landing page for the route.
    ├── guide.md
    ├── _sidebar.md            => http://domain.com 
    └── zh-cn
        ├── README.md          => use docs/_sidebar.md as sidebar
        └── guide.md           => http://domain.com/#/zh-cn/
         
```

Specify alias to avoid unnecessary fallback.
```html
<script>
  window.$docsify = {
    loadSidebar: true,
    alias: {
      '/.*/_sidebar.md': '/_sidebar.md'
    }
  }
</script>
```
### Set Page Titles from Sidebar Selection

!> It seems not working? 
A page's title tag is generated from the selected sidebar item name. For better SEO, you can customize the title by specifying a string after the filename.
```markdown
<!-- docs/_sidebar.md -->
* [Home](/)
* [Guide](guide.md "The greatest guide in the world")
```

### Table of Contents

It automatically generate a table of contents by setting a `subMaxLevel`.

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadSidebar: true,
    subMaxLevel: 2
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

## This is an example <!-- {docsify-ignore} -->

Ignore a specific header by `<!-- {docsify-ignore} -->`

Ignore all headers on a specific page by `<!-- {docsify-ignore-all} -->`

```
# Getting Started <!-- {docsify-ignore-all} -->

## Header <!-- {docsify-ignore} -->

This header won't appear in the sidebar table of contents.
```

## Custom Navbar

### HTML
```html
<!-- index.html -->

<body>
  <nav>
    <a href="#/">EN</a>
    <a href="#/zh-cn/">中文</a>
  </nav>
  <div id="app"></div>
</body>
```
### Markdown
```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadNavbar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```
```markdown
<!-- _navbar.md -->

* [En](/)
* [chinese](/zh-cn/)
```
!> `_navbar.md` has the same characteristic as `_sidebar.md`, create a `.nojekyll` in `./docs` to prevent GitHub Pages from ignoring files that begin with an underscore.
### Nesting
Here is an example of this site.
``` markdown
<!-- _navbar.md -->

* [:us:](/)
* [:cn:](/zh-cn/)

* Quick Link

    * [Codes](codes/README.md)
    * [Notes](notes/README.md)
    * [Projects](projs/README.md)

```
### navbar with the emoji plugin
above navbar is an example that use the emoji plugin
```html
<!-- index.html -->

<script>
  window.$docsify = {
    // ...
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
```
```markdown
<!-- _navbar.md -->

* [:us:](/)
* [:cn:](/zh-cn/)
```

## Cover page


## Plugins

### [docsify-katex](https://github.com/upupming/docsify-katex)

A docsify plugin for rendering LaTex math equations [@upupming](https://github.com/upupming).

#### Usage

Add docsify-katex CDN to your index.html:
```html
<!-- CDN files for docsify-katex -->
<script src="//cdn.jsdelivr.net/npm/docsify-katex@latest/dist/docsify-katex.js"></script>
<!-- or <script src="//cdn.jsdelivr.net/gh/upupming/docsify-katex@latest/dist/docsify-katex.js"></script> -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/katex@latest/dist/katex.min.css"/>
```

[Supported functions](https://upupming.site/docsify-katex/docs/#/supported)

### [docsify-count](https://github.com/827652549/docsify-count)

This is a plugin to add word count for markdown files of docsify.
#### Usage 
```html
<script src="//unpkg.com/docsify-count/dist/countable.min.js"></script>

or

<script src="https://cdn.jsdelivr.net/npm/docsify-count@latest/dist/countable.min.js"></script>
```
Setting
```html
window.$docsify = {
  count:{
    countable: true,
    position: 'top',
    margin: '10px',
    float: 'right',
    fontsize:'0.9em',
    color:'rgb(90,90,90)',
    language:'chinese',
    localization: {
      words: "",
      minute: ""
    },
    isExpected: true
  }
}
```

### Write a plugin

A plugin is simply a function that takes `hook` as an argument. The hook supports handling of asynchronous tasks. 
[👉official document👈](https://github.com/docsifyjs/docsify/blob/314e2d9d39a024270403a42eb19bd98e6cce8d17/docs/write-a-plugin.md)

```html
window.$docsify = {
  plugins: [
    function(hook, vm) {
      hook.init(function() {
        // Called when the script starts running, only trigger once, no arguments,
      });

      hook.beforeEach(function(content) {
        // Invoked each time before parsing the Markdown file.
        // ...
        return content;
      });

      hook.afterEach(function(html, next) {
        // Invoked each time after the Markdown file is parsed.
        // beforeEach and afterEach support asynchronous。
        // ...
        // call `next(html)` when task is done.
        next(html);
      });

      hook.doneEach(function() {
        // Invoked each time after the data is fully loaded, no arguments,
        // ...
      });

      hook.mounted(function() {
        // Called after initial completion. Only trigger once, no arguments.
      });

      hook.ready(function() {
        // Called after initial completion, no arguments.
      });
    }
  ]
};
```
!> You can get internal methods through window.Docsify. Get the current instance through the second argument.

## Customization

### formatUpdated and docsify-updated

- type: String|Function
- We can display the file update date through `{docsify-updated}` variable. And format it by `formatUpdated`.
- https://github.com/lukeed/tinydate#patterns

```html
window.$docsify = {
  formatUpdated: '{MM}/{DD} {HH}:{mm}',
  plugins: [
    function(hook, vm) {
      hook.beforeEach(function(html) {
        return (
          html +
          '\n----\n' +
          'Last modified {docsify-updated} ' 
        );
      });
    }
  ]
};
```


### Table

<table>
    <thead>
        <tr>
            <th>Layer 1</th>
            <th>Layer 2</th>
            <th>Layer 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=4>L1 Name</td>
            <td rowspan=2>L2 Name A</td>
            <td>L3 Name A</td>
        </tr>
        <tr>
            <td>L3 Name B</td>
        </tr>
        <tr>
            <td rowspan=2>L2 Name B</td>
            <td>L3 Name C</td>
        </tr>
        <tr>
            <td>L3 Name D</td>
        </tr>
    </tbody>
</table>

