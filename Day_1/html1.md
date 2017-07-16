# Contents

- <a href="#one">HTML layout</a>
- <a href="#two">Hello, world!</a>
- <a href="#three">Using comments</a>
- <a href="#four">Some common HTML elements</a>
- <a href="#five">Keeping things DRY with partials</a>

---

# Let's get coding

You've got all of your developer tools set up, and you're ready to start coding. As a front end developer, typically the first place you'll begin is with the 'bare bones' of your project; the HTML page structure.

In the Terminal, while within the folder containing your `index.html`, type `subl .` to open your project with Sublime Text.

# <span id="one">1. HTML layout</span>

HTML files are typically laid out as such:

```html
  <!DOCTYPE html>
  <html>
    <head>
      // content in the head goes here. This usually involves things like CSS / JavaScript links,
      // the title of the page, etc.
    </head>
    <body>
      // Body content goes here.
    </body>
  </html>
```

Let's go through these one-by-one.

  - `<!DOCTYPE html>` tells the browser what type of code to expect.
  - The `<html></html>` tags enclose all of the HTML on our page, and tell the browser where to start and stop reading the code.
  - The `<head>` tags contain all of the HTML code which doesn't make up the body of the web page. Commonly found within the head tags are things like stylesheet links and 'metadata', such as the title of the page which shows up n the browser tab.
  - The`<body>` tags contain the meat of the page; here's where we'll declare all of the components making up the visual structure of the page.

# <span id="two">2. Hello, world!</span>

Now to get something showing up in our browser. Right-click `index.html` in the Sublime sidebar and select 'Open in Browser > Chrome'. It should just be a blank screen.

# <span id="three">4. Using comments</span>

Comments are a great way to kind of 'signpost' your code. Think of them as sticky notes you might put on a book.

# <span id="four">5. Some common HTML elements</span>

- 'semantic' elements; eg, headers.

# <span id="five">6. Keeping things DRY with partials</span>

Typically a header will be displayed constantly across all pages on a single site. Trouble is, if we want that to be the case here, we'll have to copy and paste the header code into all pages of our site. Not only is that kind of a pain, it's also bad coding practice.

[The 'DRY' Principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) states that we should do something to reduce unnecessary code repetition. Ideally what we'd like to do here is write the code for the header once and have it generate on every page. We're going to do that with something known as a `template engine`.