![Sass](../img/day_3/sass.png)

# What is Sass?

Sass (Syntactically Awesome Stylesheets), is an _extension_ to CSS; think of it as an added layer of complexity. Using Sass allows us to do loads of cool, advanced stuff in CSS, such as:

- Storing common colours and elements in variables,
- Nesting styles, 
- And reusing code between selectors without having to repeat yourself.

# Installing Sass into our project

Sass requires a bit of set up for us to get started.

1. We need to get our project initiated with `npm`. In the `Terminal` and while in your project folder, type `npm init`. The Terminal will ask you a lot of questions, but you don't need to change any of the defaults.

2. In `Terminal`, type `npm install -g node-sass`.

# Gulp : What and Why?

<img src="../img/day_3/gulp.png">

Gulp is a 'Task runner', a tool that helps you out with several tasks when it comes to web development. It's often used to do front end tasks like:

- Spinning up a web server
- Reloading the browser automatically whenever a file is saved
- Using preprocessors like Sass or LESS
- Optimizing assets like CSS, JavaScript, and images

We're going to use gulp to process our `scss` files, and turn them into `css` that the browser can use.

## Getting Gulp set up

1. `npm install -g gulp` installs Gulp globally.
2. If there is no `package.json` file in your project directory running `npm init` will create one. Use it with `-y` to skip the questions.
3. `npm install --save-dev gulp` installs Gulp locally. `--save-dev` adds gulp to devDependencies in package.json.
4. `npm install gulp-sass --save-dev` installs gulp-sass locally.

5. Setup gulp for your project by creating a `gulpfile.js` file in your project root folder:

`touch gulpfile.js`

 with this content:


```js
'use strict';
var gulp = require('gulp');
var sass = require('gulp-sass');
gulp.task('sass', function () {
  gulp.src('./sass/**/*.scss')
    .pipe(sass().on('error', sass.logError))
    .pipe(gulp.dest('./css'));
});
```

`gulp sass` runs the above task which compiles .scss file(s) in the sass folder and generates .css file(s) in the css folder.

To make life easier, let's add a watch so we don't have to compile it manually. Add this code to your  gulpfile.js:

```js
gulp.task('sass:watch', function () {
  gulp.watch('./sass/**/*.scss', ['sass']);
});
```

All is set now! Just run the watch task:

`gulp sass:watch`

# Writing some Sass

## Variables

Variables are a form of shorthand; we can 'save' propeties in codewords, which we can then stick anywhere in our Sass sheets.

```css
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

## Nesting

In HTML, we nest tags so that elements which are nested are the 'children' of their parent elements.

In CSS, there's no nesting; each style needs to be standalone. This can lead to a lot of repetition...

```css

header {
  ...
}

header ul li {
  ...
}

header ul li a {
  ...
}
```

But in Sass, we can nest these selectors:

```cs
header {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

See how it's already so much easier and cleaner?

## Partials

Here's one of my personal favourite features of Sass: Partials.

You can create partial Sass files that contain little snippets of CSS that you can include in other Sass files. This is a great way to modularize your CSS and help keep things easier to maintain. A partial is simply a Sass file named with a leading underscore. You might name it something like `_partial.scss`. The underscore lets Sass know that the file is only a partial file and that it should not be generated into a CSS file. Sass partials are used with the `@import` directive.

CSS has an `import` option that lets you split your CSS into smaller, more maintainable portions. The only drawback is that each time you use `@import` in CSS it creates another HTTP request. Sass builds on top of the current CSS `@import` but instead of requiring an HTTP request, Sass will take the file that you want to import and combine it with the file you're importing into so you can serve a single CSS file to the web browser.


Let's say you have a couple of Sass files, `_reset.scss` and `base.scss`. We want to import `_reset.scss` into base.scss.

`reset.scss`:

```css
// _reset.scss

html,
body,
ul,
ol {
  margin:  0;
  padding: 0;
}
```

```css
// base.scss

@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

`@import` pulls the contents of `reset.scss` into `base.scss`.

## Extend/Inheritance

This is one of the most useful features of Sass. Using `@extend` lets you share a set of CSS properties from one selector to another. It helps keep your Sass very **DRY** (remember; DRY stands for 'Don't Repeat Yourself'). In our example we're going to create a simple series of messaging for errors, warnings and successes.

```css
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}

.warning {
  @extend .message;
  border-color: yellow;
}
```

What the above code does is allow you to take the CSS properties in .message and apply them to `.success`, `.error`, & `.warning`. The magic happens with the generated CSS, and this helps you avoid having to write multiple class names on HTML elements. This is what it looks like:

```css
.message, .success, .error, .warning {
  border: 1px solid #cccccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```