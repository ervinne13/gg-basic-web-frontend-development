# Webpack Basics

As mentioned by the instructor, managing your own build tools is a must nowadays for JavaScript developers. Learning at least the basics of webpack will really help you land your first job in frontend or JavaScript development.

## Dependencies

If you haven't installed node yet, download it and install from [nodejs.org](https://nodejs.org/en/).
You'll also need to install the node package manager (npm).

```bash
npm install -g
```

## Enabling Webpack

Create a new folder where you will be working on the project, in this example we'll create a new folder called `webpack-basics`. Move inside that folder and start up your terminal.

Execute the command:
```bash
npm init
```

This will ask you a series of questions, set the name to "webpack-basics" and author to your name and email (Format: Name \<email\>) and press enter through all else to leave it at default.

It should generate a `package.json` file that contains the following:

```json
{
  "name": "webpack-basics",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Ervinne Sodusta <ervinne.sodusta@nuworks.ph>",
  "license": "ISC"
}
```

__Add Webpack using the command:__

```bash
npm install -D webpack webpack-cli
```

This gets 3 things to happen:
- The name Webpack gets added as a dev dependency inside the package.json file (that’s what the -D in the command is for). This tells the project that Webpack is a tool we will use in the development process, not on the actual website.
- A new folder called node_modules gets added to the project.
- Webpack (a folder of files) appears inside of node_modules.

The same thing happens with webpack-cli, this dependency contains cli commands we can use to actually run webpack.

__Add Webpack as a script__

Update the `scripts` portion of your `package.json` and add the following:

```json
"scripts": {
  "build": "webpack",
  "start": "webpack --watch"
},
```

## Creating a Demo Project

- Let's create a folder called `src` in the root of the project.
- Inside that folder, create a file called `index.js`. This is where we will point all of our js and css/scss files.
- Create an `index.html` file in the root of the project with the following content:

```html
<html>
    <head>
        <title>My Webpack App</title>
    </head>
    <body>
        We'll put some content here

        <script type="text/javascript" src="dist/bundle.js"></script>
    </body>
</html>
```

Notice that we don’t include the `src/index.js` that we just created, but `dist/bundle.js`. This file actually doesn’t exist yet. It’s what Webpack’s going to create for us.

## Configuring Webpack

Create a new file called `webpack.config.js` in the root of your project with the following contents:

```js
const path = require('path');

module.exports = {
    entry: './src/index.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    }
};
```

__Entry and output__

- __Entry__: Like the file and folder we just created, the entry file is called `index.js` and lives inside the folder `src`. This tells webpack what file to use to generate your intended output
- __Output__: This is where Webpack will place all the ready files. The file will be named `bundle.js` and appear inside the folder dist (distribution).

You can change the names to whatever you prefer, as long as they are in sync between webpack.config.js, files, folders and the linked script in the HTML.

## Loading Through Imports

Now, let’s create some code for Webpack to work with.

- Go to the folder src and make a new folder called `js`.
- Inside `js`, make a JavaScript file called `sub-module1.js`.
- Write some JavaScript in `sub-module1.js`, for example:

```js
    console.log("Hi, I'm a submodule loaded using webpack");
```
- Repeat the same process but with a `sub-module2.js` file. Update the corresponding console message.
- Import the two files in the `index.js` with:

```js
import './sub-module1.js';
import './sub-module2.js';
```

- Finally, we can build our app by running in our terminal:

```bash
npm run build
```

Now, check your project and it should now contain a new `dist` folder containing the files we just built.

When you open index.html in a browser, open Developer Tools and look in the console. You will see that it shows the console messages from both the files we imported.

## Problematic Relative Imports

This is a very common issue in JavaScript development. Imports are relative, this means you will have awkward navigation in your imports if you have deep folders in place. To demonstrate this problem, let's say the we have divided our code by feature and each feature can import from one another.

Create the following files & folders:

    - src/features/common/panel.js
    - src/features/profile/page.js

- Inside `panel.js` is:
```js
console.log("I'm panel.js");
```

- and in `profile.js`:
```js
import '../common/panel';
```

- finally, update `index.js` to:

```js
import 'features/profile/page';
```

- Build and test your page in the browser. This works, but notice the import in `profile.js`. We'll have to navigate through the folder structure relatively. This is generally not desirable.

### Enabling Root Imports & Aliases

We can enable an aliases in webpack to resolve this. In your `webpack.config.js` file, add the following code:

```js
resolve: {
    alias: {
        features: path.resolve(__dirname, 'src/features')
    }
},
```

With this in place, we can update the import from:
```js
import '../common/panel';
```
to:
```js
import 'features/common/panel';
```

## Webpack Loaders

For every kind of file (JavaScript, TypeScript, CSS, SCSS, etc), webpack needs some kind of loader to interpret it. In our previous example, we havent specified it but webpack automatically uses an es6 loader which enables us the `import` syntax (normally you only get `require` - an es5 feature).

First, let's install the dependencies we will be needing:

```bash
npm install -D sass-loader node-sass style-loader css-loader
```

We will be making use of this variable later on when we add rules.

Webpack can't read scss files by default, we need to tell it to be able to by adding the following rules in our `webpack.config.js`:

```js
module: {
    rules: [
        {
            test: /\.scss$/,
            use: [
                "style-loader",
                "css-loader",
                "sass-loader"
            ]
        }
    ]
},
```

This is the simplified version of how you can make use of loaders. The full documentation of using sass loaders can be found [here](https://github.com/webpack-contrib/sass-loader).

## Adding Sass

- First, let's prepare our HTML to load our bundled style by adding the following inside the `head` tag:

```html
<link rel='stylesheet' href='dist/style.css'>
```

- Then, write our first sass file in `src/scss/base.scss` with the following contents:

```scss
$bg-color: pink;
body {
    background: $bg-color;
}
```

- Then add the following to `src/app.js` to import our sass file:

```js
import 'scss/base.scss'
```

- We'll be needing an alias for `scss` folder so add it in `webpack.config.js`:
```js
scss: path.resolve(__dirname, 'src/scss')
```

## (Ab)using Imports for Modular Styling

The nice thing about this is that we can separate our `scss` files per feature. Meaning each feature (as we seen earlier, `common` and `profile` can have their own individual styles). We don't have to manage very large chunks of css or scss files.

Keep this in mind as we will be (ab)using this later on when working on our project.

## Webpack Templates & Multiple Pages

What we've done so far is good for single page applications/websites. You will usually create projects with multiple pages as well. To also generate html files, we'll need to install:

```bash
npm install -D html-webpack-plugin
```

Import this in our `webpack.config.js` by adding this at the top of your file:

```js
const HtmlWebpackPlugin = require('html-webpack-plugin')
```

... so that we can use it to generate an html file for us by adding it in the `plugins`:

```js
plugins: [
    new HtmlWebpackPlugin()
]
```

This will ignore our `index.html` from before and create a new one that automatically imports the files that we need (instead of having us set the import manually). So delete the `index.html` at the root folder.

Test by running build:

```bash
npm run build
```

### Adding Content by Using Templates

But now we can't control the content of the pages since it's automatically generated.
We can do so by creating templates. Create a new `index.html` file, but this time, inside `src` folder with the contents:

```html
<html>
    <head>
        <meta charset="utf-8"/>
        <title><%= htmlWebpackPlugin.options.title %></title>
    </head>
    <body>
        <h1>I'm the new index page</h1>
    </body>
</html>
```

Notice that with templates, we don't have to manually specify the `<script>` tags to import the js file that was bundled. Moreover, notice the script:

```html
<title><%= htmlWebpackPlugin.options.title %></title>
```

This is templating language in webpack where we can "insert" variables into.

Now, to actually use this as the template of `index.html`, update your `webpack.config.js` file's `plugins` to:

```js
plugins: [
    new HtmlWebpackPlugin({
        title: 'My Custom Template',
        template: './src/index.html'
    })
],
```

Build again and it should use the template you specfied.

### Creating a Secondary Page

Let's say we're going to create a second page called `about.html` that contains information about your website.

Create the following files:

- `src/features/about/page.html`
- `src/features/about/page.scss`

Notice that this now contains its own `scss` style. This way, we can isolate styles that are only really needed by this page, making debugging and maintainance later on easier. Update the content of each file with:

File `src/features/about/page.html`:
```html
<html>
    <head>
        <meta charset="utf-8"/>
        <title><%= htmlWebpackPlugin.options.title %></title>
    </head>
    <body id="about-page-body">
        <h1>I'm the about page, my background should be blue</h1>
        <a href="index.html">Back to home page</a>
    </body>
</html>
```

File `src/features/about/page.scss`:
```scss
$bg-color: #7096F6;
body#about-page-body {
    background: $bg-color;
}
```

Then add a plugin entry in our `webpack.config.js`:

```js
new HtmlWebpackPlugin({
    title: 'About Page',
    template: './src/features/about/page.html'
}),
```

Then update the `index.html` template so that we can have a link to the about page. Add the following to the body of the file:

```html
<a href="about.html">Go to About Page</a>
```

Now we're able to create multiple pages that can navigate through each other. One problem though, is that the background color of the about page isn't blue but is still pink.

This is because we haven't told webpack to load it's scss file.

We have two ways to import this, one way is to add it in the `app.js` file.

```js
import 'features/about/page.scss';
```

Add it and it should be working now. But that defeats the purpose of separating it by feature since we'll have to add each dependencies in the app.js. Doing that makes things not modular anymore.

To resolve this, we can make use of "chunks"

### HtmlWebpackPlugin Chunks

To create multiple chunks, we'll have to create multiple entries first. Update the `entry` and `output` of our `webpack.config.js` to:

```js
entry: {
    app: './src/app.js',
    about_scss: './src/features/about/page.scss',
},
output: {
    path: path.resolve(__dirname, 'dist'),
    filename: "[name].bundle.js"
},
```

... and update the `HtmlWebpackPlugin` of the About Page to:

```js
new HtmlWebpackPlugin({
    title: 'About Page',
    filename: 'about.html',
    template: './src/features/about/page.html',
    inject: 'body',
    chunks: [ 'about_scss' ]
}),
```

Notice that we also updated the filename to be dynamic such that it would generate multiple bundles depending on the name (key in the `entry` object).

Inspect the generated `about` page and you should see that it generates two `<script>` imports, one for the `app` (our base scss) and the `about`.

This is still not quite maintainable though as everytime we add a page in the features, we'll have to add its chunks.

### Developing a Dynamic Page Loader

We can create a dynamic page loader that can read files in a registry of pages per feature we define. Let's first create a configuration that's easier to manage. Create a new file `config/page-registry.js` with the contents:

```js
module.exports = [
    {        
        feature: 'about',
        variables: {
            title: 'About Page'
        }
    }
];
```

Here, whenever we need to register a new page in the `features` folder, we just have to specify the folder name we gave it and the variables that it needs (in this case, just `title`).

Then we develop the page loader. Create a new file `lib/page-registry-loader.js`. Follow the instructor as he creates this manually for you to better understand. At the end of it, it should contain:

```js

const HtmlWebpackPlugin = require('html-webpack-plugin');
const pageRegistry = require('../config/page-registry');
const fs = require('fs')

let entries = {};
let plugins = [];

exports.load = function() {
    pageRegistry.map(page => {
        const scssEntry = generateEntry(page, 'scss');
        const jsEntry = generateEntry(page, 'js');
        let pageChunks = [ 'app' ]; // default chunk as defined in entry

        if (scssEntry) {
            entries[scssEntry.key] = scssEntry.path;
            pageChunks.push(scssEntry.key);
        }

        if (jsEntry) {
            entries[jsEntry.key] = jsEntry.path;
            pageChunks.push(scssEntry.key);
        }
        
        plugins.push(generatePlugin(page, pageChunks));
    });
};

function generateFolder(page) {
    return `./src/features/${page.feature}`;
}

function generateEntry(page, ext) {
    const folder = generateFolder(page);
    const file = `${folder}/page.${ext}`
    if (fs.existsSync(file)) {
        return {
            key: `${page.feature}_${ext}`,
            path: file
        };
    }

    return false;
}

function generatePlugin(page, pageChunks) {
    const folder = generateFolder(page);
    const template = `${folder}/page.html`;

    return new HtmlWebpackPlugin(Object.assign({        
        filename: `${page.feature}.html`,
        template: template,
        inject: 'body',
        chunks: pageChunks
    }, page.variables));
}


exports.getGeneratedEntries = function() {
    return entries;
};

exports.getGeneratedPlugins = function() {
    return plugins;
}
```

Then make use of this loader in the `webpack.config.js` file. Updated it to:

```js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const pageRegistryLoader = require('./lib/page-registry-loader');

pageRegistryLoader.load();

let entry = Object.assign({
    app: './src/app.js'
}, pageRegistryLoader.getGeneratedEntries());

let plugins = [
    new HtmlWebpackPlugin({
        title: 'My Custom Template',
        template: './src/index.html'
    }),
].concat(pageRegistryLoader.getGeneratedPlugins());

module.exports = {
    entry: entry,
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: "[name].bundle.js"
    },
    module: {
        rules: [
            {
                test: /\.scss$/,
                use: [
                    "style-loader",
                    "css-loader",
                    "sass-loader"
                ]
            }
        ]
    },
    plugins: plugins,
    resolve: {
        alias: {
            features: path.resolve(__dirname, 'src/features'),
            scss: path.resolve(__dirname, 'src/scss')
        }
    },
};
```

Now try adding configurations or a `page.js` or `page.scss` files in those folders you add and it will automatically be built.

IMPORTANT: You should remember that you should only really use this approach if your application gets big. Normally importing your dependencies in the main `app.js` works well and is actually performaning faster especially for small applications or single page applications/web pages.

## Common Markup & Reusing Code

Perhaps the most important part of being able to build your markup is to enable common markup. Consider an HTML file that has a header, footer, and a navigation. All of those components are also present in other html files/pages. Repeating code will hurt maintainability of your application so you should have separate markup for each.

### Creating a Common Header

Let's first create a (very simple) header in `src/features/header/component.html` with the content:

```html
<header>
    <h1>I'm the page header, I'll be present on all page</h1>
</header>
```