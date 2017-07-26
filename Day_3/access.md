# Considering our User's needs

When designing and creating web pages, it's important that the web pages are accessible to all audiences. In particular, due to the visual and dynamic nature of the webpages that you’ll be making, it’s important to make sure that your website will also make sense to visually-impaired or blind users.

Many visually-impaired or blind users access web pages with the help of screen readers. Screen readers parse through the HTML of your web page and read the contents out loud, responding to commands to navigate around the page, and take actions such as clicking on a link, typing in an input field, or submitting a form. In this resource, we’ll give an overview of a few ways that you can improve the accessibility of your web page and help screen readers better interpret it!

# Color on your site

Maintaining a high colour contrast is vital to making your site accessible. The Web Accessibility Guidelines suggest maintaining 4:5:1 as the minimum contrast ratio. For standard sized text the ideal ratio would be 7:1. Ideally, text needs to be in black and the background white.

There are some great, useful tools to help Developers keep their sites accessible, such as [Colorsafe](http://colorsafe.co/).

# ALT text

One way to make the elements of your page more comprehensible to screen readers is to provide alt text for images. Alt, or alternative, text is provided as an attribute to the `<img>` tag to describe the image to the screen reader. For instance, when encountering the below...

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My First Web Page!</title>
  </head>
  <body>
    <img src="https://en.wikipedia.org/wiki/File:Brown_bear.jpg" alt="A brown bear"/>
  </body>
</html>
```

...the screen reader will be able to read aloud the description of the image ("A brown bear") to the user, as opposed to simply informing the user that an image exists on the page. Be sure to provide succinct alt text descriptions for each image on your web page!

# Semantic tags

As we think about styling text on a webpage, you might have noticed some overlap between the following pairs of tags:

`<b>` vs. `<strong>`
`<i>` vs. `<em>`

If you ever try swapping one of the tags in a pair for the other, you’ll most likely see that there’s little to no change in how the page looks. Both the `<b>` and `<strong>` tags bolden text, and the `<i>` and `<em>` italicize text. However, there’s a fundamental difference between each of the tags in a pair when it comes to accessibility!

The `<b>` and `<i>` elements simply denote how the text should look: text within these tags should appear as bold or italicized, respectively.

`<strong>` and `<em>`, however, denote how text should be understood and, though they result in the same visual appearance, they affect how the screen reader interprets them: text within these tags are read out with a different voice to indicate the emphasis for each. These tags are known as semantic tags.

So although `<strong>` and `<em>` result in visually similar text as `<b>` and `<i>`, they provide a way for screen readers to communicate the parts of text that are already highlighted visually to the user.

# ARIA

ARIA stands for 'Accessible Rich Internet Applications', and defines ways to make Web content and Web applications (especially those developed with Ajax and JavaScript) more accessible to people with disabilities. For example, ARIA enables accessible navigation landmarks, JavaScript widgets, form hints and error messages, live content updates, and more.

ARIA attributes are designed to be interpreted automatically by the browser and translated to the operating system's native accessibility APIs. When ARIA is present, assistive technologies are able to recognize and interact with custom JavaScript controls in the same way that they do with desktop equivalents. This has the potential for providing a much more consistent user experience than was possible in the previous generation of web applications, since assistive technology users can apply all of their knowledge of how desktop applications work when they are using web-based applications.

Compare:

```html
<div>
  <div id="ch1Panel">Chapter 1 content goes here</div>
  <div id="ch2Panel">Chapter 2 content goes here</div>
  <div id="quizPanel">Quiz content goes here</div>
</div>
```

To:

```html
<div>
  <div id="ch1Panel" role="tabpanel" aria-labelledby="ch1Tab">Chapter 1 content goes here</div>
  <div id="ch2Panel" role="tabpanel" aria-labelledby="ch2Tab">Chapter 2 content goes here</div>
  <div id="quizPanel" role="tabpanel" aria-labelledby="quizTab">Quiz content goes here</div>
</div>
```