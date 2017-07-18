# Contents

- <a href="#one">HTML layout</a>
- <a href="#two">Hello, world!</a>
- <a href="#three">Using comments</a>
- <a href="#four">Fleshing out our page</a>
- <a href="#five">Linking stylesheets in HTML pages</a>

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
  - The `<html></html>` tags enclose all of the HTML on our page and tell the browser where to start and stop reading the code.
  - The `<head>` tags contain all of the HTML code which doesn't make up the body of the web page. Commonly found within the head tags are things like stylesheet links and 'metadata', such as the title of the page which shows up n the browser tab.
  - The`<body>` tags contain the meat of the page; here's where we'll declare all of the components making up the visual structure of the page.

# <span id="two">2. Hello, world!</span>

Now to get something showing up in our browser. Right-click `index.html` in the Sublime sidebar and select 'Open in Browser > Chrome'. It should just be a blank screen.

If we enter the following...

```html
<h1>Hello, world!</h1>
```

We should see this:

![Our first HTML element](../img/day_1/hello-world.png)

So we know that our HTML is showing up on our page just fine.

Let's put our first image in. Remove the previous `<h1>` tag and enter between the body tags:

```html
<img src="./img/lake.jpeg">
```

Note that the `<img>` tag is _self-closing_-- you don't need an accompanying `</img>` tag to tell the browser where the image ends, unlike in the heading tag we just used.

If you refresh `index.html` in your browser, you should see the image showing up. But it's pretty huge, so we'll need to resize it. We could do something like the following:

```html
<img src="./img/lake.jpeg" width="500px">
```

This at least makes the image fully visible, but it's not a great solution; ideally, we want the image to take up the whole screen. The trouble is, we don't know how big the user's screen is. For this, we'll need some CSS. We don't have any stylesheets made just yet, so we'll use some `inline CSS`:

```html
<img src="./img/lake.jpeg" style="max-width:100%;">
```

Inline CSS is when you attach the CSS styling directly to the tag of the HTML element it affects. Shortly we'll make some style sheets and move all of our stylings into there, but for now, this is a temporary solution to our image sizing problem.

# <span id="three">4. Using comments</span>

Comments are a great way to kind of 'signpost' your code. Think of them as sticky notes you might put on a book. When you 'comment out' some code, it won't affect the resulting browser code at all. So you can use code either to make code 'latent', or for your own notation purposes.

To remind ourselves to remove the inline CSS when we made our stylesheets, let's make a comment about our `img` tag now.

![Commenting in HTML](../img/day_1/html-comment.png)

# <span id="four">5. Fleshing out our page</span>

It's time to get some text into our app.

Add a `div` element beneath our image. `div` stands for 'division', but it's better to think of a div as a box. It's a container for whatever other HTML elements you want to put in that box, which you can then manipulate with CSS to get it to behave however you want. Within the div, open some paragraph tags; `<p`>, like so:

```html
<!doctype html>
<html>
  <head>

  </head>
  <body>

    <!-- NOTE : remove the inline CSS when stylesheets are made! -->
    <img src="./img/lake.jpeg" style="max-width:100%;" />

    <div>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Itaque cumque amet provident eligendi ut id, ratione quasi tenetur ipsum repellendus aperiam voluptatum eaque reiciendis, eos quae tempora temporibus magni hic?
      </p>      

      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Itaque cumque amet provident eligendi ut id, ratione quasi tenetur ipsum repellendus aperiam voluptatum eaque reiciendis, eos quae tempora temporibus magni hic?
      </p>
    </div>

  </body>
</html>
```

**Note:** you can type `lorem` and then press tab to instantly get some filler text, but if you'd like some alternative ipsum text you can check out [Choose Your Ipsum](http://idsgn.dropmark.com/107). Two of my favourites are [Hipster Ipsum](https://hipsum.co/) and [Cat Ipsum](http://www.catipsum.com/).

> If you're using Sublime Text and you want a bit more text, highlight the lines you want to duplicate (the `<p>` tags and the text within) and press `CMD + Shift + D`.

![](../img/day_1/div-text.png)

### Making a header

Every page needs a convenient form of navigation so that the user can get around the site, and typically a header is a good way to provide this. Our header will sit at the top of the page, and contain all the most vital links the user will need.

Code:

```html
<header>
  <ul>
    <li>Home</li>
    <li>About</li>
  </ul>
</header>
```

The `<header>` tag is an example of _semantic HTML_. It's a descriptive divider for the elements in our page. Other example of semantic HTML elements include `<footer>`, `<article>` and `<section`.

Inside our header section, we have the `ul` and `li` tags, which stand for 'unordered list' and 'list item' respectively.

Right now, our header items aren't pointing anywhere. Let's fix that now. 

### Making and linking to additional pages

In the `Terminal`, while in the root directory of our project, type:

```
touch about.html
```

to create our about page. For now, we'll just put some filler text in `about`:

```html
<h1>This is the about page.</h1>
```

Now that we've got two pages, we can link between them in the header. Return to `index.html`, and add `<a>` tags to the `list items`:

```html
<header>
  <ul>
    <li>
      <a href="">Home</a>
    </li>
    <li>
      <a href="">About</a>
    </li>
  </ul>
</header>
```

You may have noticed that I've moved the `<a>` tags onto a new line between the `<li>` tags, and the `<li>` tags are indented within the `<ul>` tags. Indentation is a vital part of writing **readable code**, and is considered best practice in coding. Breaking nested tags onto their own lines also helps to keep things tidy.

## Making a stylesheet

Speaking of lines, let's get our header links on a single horizontal line so that it looks nicer and takes up less vertical space. For that, we'll need to make our first CSS stylesheet:

`Terminal`:

```
mkdir css
touch css/style.css
```

**`style.css`**:

```css
header ul li {
  display: inline-block;
  list-decoration: none;
}
```

The above CSS commands the browser to look for any `li` tags within the `ul` tags, which in turn are within the `header` tag, and apply the styling within. The property-value pairs here will line the `li` elements up horizontally, and remove their bullet points.

Here's the syntax for writing CSS rules:

![How to write CSS](../img/day_1/css-syntax.jpg)

Your project file structure should now look like this:

![File structure](../img/day_1/file-structure.png)


# <span id="five">Linking stylesheets in HTML pages</span>

In order for our new CSS to apply to our HTML, we'll need to make a `<link>` tag in the `<head>` of our `index.html` page.

`index.html`:

```html
<head>
  <link rel="stylesheet" href="./css/style.css">
</head>
```

Refresh your page in Chrome, and you should see the style apply to your header.

All that's left to do now is to show the `anchor (<a>)` tags where to point:

```html
<header>
  <ul>
    <li>
      <a href="./index.html">Home</a>
    </li>
    <li>
      <a href="./about.html">About</a>
    </li>
  </ul>
</header>
```

If you head back to your page in Chrome, you'll now see that the header list items are links, and you can now move between your pages.

We won't be doing anything with the about page until we're doing styling `index`, so here we can just put a link back to the homepage:

```html
<a href="./index.html">Home</a>
```

> **NOTE** <br />
> We've made some pretty significant changes to our project, so now would be a good time to commit them.

> 1. Type `gst` to see our changes.
> 2. `git add .` to add all of our changes to staging.
> 3. `git commit -m "Made header element"` to write the commit message and make the commit.
> 4. `git push` to push our update to GitHub.

Now let's move on to continuing to build out our HTML, and styling it up.

