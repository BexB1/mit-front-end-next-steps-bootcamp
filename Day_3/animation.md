# CSS Animations

## Transform effects

Let's add a `:hover` pseudo-class to our buttons:

```css
/* BUTTONS */

.hero-btn {
  display: inline-block;
  color: #FFF;
  border: 3px solid #FFF;
  border-radius: 50px;
  padding: 10px 30px;
}

.hero-btn:hover {
  border: 3px solid none;
  color: #33584C;
  background-color: #fff;
}
```

Now, when the button is hovered over by the mouse cursor, it's appearance will change. We can take it a bit further, however, by adding the transform method:

```css
transform: scale(1.2);

```

Now the button willl change colour, and grow. But let's smoothen out that animation effect:

```css
transition: all 0.35s ease;
```

Nice!

## Parallax

Let's go ahead and add the following styles to our `.hero` class:

```css
background-position: 50% 50%;
background-repeat: no-repeat;
background-attachment: fixed;
background-size: cover;
```

... Now head back to `index`, and refresh. Try scrolling up and down - you should see the Parallax effect. Cool, right?

## Useful links

- [CSS Tricks : Animation](https://css-tricks.com/almanac/properties/a/animation/)