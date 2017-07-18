# Contents

- <a href="#one">What is Bootstrap?</a>
- <a href="#two">Installing Bootstrap</a>
- <a href="#two">Working with the Bootstrap Grid</a>
- <a href="#two">Helpful classes</a>
- <a href="#two">Using components</a>

---

# <span id="one">What is Bootstrap?</span>

Bootstrap is a HTML, CSS and JavaScript framework which offers a huge list of design methods and components for making the front end of your app. It allows for the easy creation of a fully responsive and attractive site.

# <span id="two">Installing Bootstrap</span>

We need to use `npm` to install Bootstrap.

`Terminal`:

```
npm install --save bootstrap@4.0.0-alpha.6
```

As usual, we need to link to bootstrap to apply it to our site.

`index.html`:

```html
<head>
  <link rel="stylesheet" href="./node_modules/bootstrap/dist/css/bootstrap.min.css">
  <link rel="stylesheet" href="./css/style.css">
</head>
```

You may notice that the link to `normalize` is gone. This is because Bootstrap has it's own CSS reset built-in. So we can remove `normalize` now, and delete the file in the terminal:

`Terminal`:

```
rm -rf css/normalize.css
```

# Working with the Bootstrap Grid

We can add our first Bootstrap class to our text div like so:

```html
<div class="container">
  <p>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Itaque cumque amet provident eligendi ut id, ratione quasi tenetur ipsum repellendus aperiam voluptatum eaque reiciendis, eos quae tempora temporibus magni hic?
  </p>      

  <p>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Itaque cumque amet provident eligendi ut id, ratione quasi tenetur ipsum repellendus aperiam voluptatum eaque reiciendis, eos quae tempora temporibus magni hic?
  </p>
</div>
```

The `.container` class centers the content horizontally, in a fixed-width box. It also prepares the content for the use of the Bootstrap grid system. Change your code as follows:

```html
<div class="container">
  <div class="row">
    <div class="col-md-6">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Itaque cumque amet provident eligendi ut id, ratione quasi tenetur ipsum repellendus aperiam voluptatum eaque reiciendis, eos quae tempora temporibus magni hic?
      </p>  
    </div>    
    <div class="col-md-6">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Itaque cumque amet provident eligendi ut id, ratione quasi tenetur ipsum repellendus aperiam voluptatum eaque reiciendis, eos quae tempora temporibus magni hic?
      </p>
    </div>
  </div>
</div>
```

Your text should now be in two columns like so:

[[IMAGE]]


