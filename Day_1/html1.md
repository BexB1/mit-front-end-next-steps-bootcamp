# Contents

- <a href="#one">Making the 'skeleton' of our project</a>
- <a href="#two">Good HTML layout</a>
- <a href="#three">All about linking</a>
- <a href="#four">Using comments</a>
- <a href="#five">Some common HTML elements</a>
- <a href="#six">Keeping things DRY with partials</a>

---

# Let's get coding

You've got all of your developer tools set up, and you're ready to start coding. As a front end developer, typically the first place you'll begin is with the 'bare bones' of your project; the HTML page structure.

# <span id="one">1. Making the 'skeleton' of our project</span>

Open `terminal` and navigate to where you'd like your project to be stored. The Desktop is a good place to keep it. 

type `touch index.html` in the root directory of your project. Remember; if you're not sure where you are currently in the terminal, you can type `pwd` for the address.

# <span id="two">2. Good HTML layout</span>

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

# <span id="three">3. All about linking</span>

- Mailto

# <span id="four">4. Using comments</span>

Comments are a great way to kind of 'signpost' your code. Think of them as sticky notes you might put on a book.

# <span id="five">5. Some common HTML elements</span>

- 'semantic' elements; eg, headers.

# <span id="six">6. Keeping things DRY with partials</span>

Typically a header will be displayed constantly across all pages on a single site. Trouble is, if we want that to be the case here, we'll have to copy and paste the header code into all pages of our site. Not only is that kind of a pain, it's also bad coding practice.

[The 'DRY' Principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) states that we should do something to reduce unnecessary code repetition. Ideally what we'd like to do here is write the code for the header once and have it generate on every page. We're going to do that with something known as a `template engine`.