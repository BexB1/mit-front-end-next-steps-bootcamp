# Functions

We've been writing code that performs different actions, but sometimes you want to group code together to achieve a particular end. This is where functions come in.

A function is a block of code designed to perform a particular task. A function is executed when it is "invoked".

The syntax of a function looks like this:

```js
function functionName (parameters) {
  // code to be executed
}
```

You can call a function whatever you want, just like a variable. You can also give a function different values every time you run it which are called "parameters".

To make the function run, we invoke it like so:

```js
functionName();
```

### Try it out

Let's write a function that adds two numbers together. We'll call it `add`. We want to add together two different numbers every time, so let's define two parameters to represent this, `x` and `y`.

```js
function add (x, y) {
  // code to be executed
}

add(2, 3);
```

Notice I've invoked the function underneath, with the paremeters `2` and `3`. Inside the function, try to `console.log()` your parameters and see what happens.

Now, we want to add these two numbers together, but it isn't enough just to write `x + y`, since we haven't told the function to return anything. It's time for a `return` statement. The `return` statement specifies the value to output.

```js
function add (x, y) {
  return x + y;
}

add(2, 3);
```

Run this code, and hopefully you get the right answer!

> **Exercise**
>
> Write a function called `multiply` that multiplies two numbers together. It should take two numbers as parameters and return the answer.

# ES6 - 'Fat arrow' functions
ES6 introduced a new way of structuring functions; the arrow function. Let's compare it against the ES5 syntax:

  ```js

  // ES5
  var multiply = function(x, y) {
    return x * y;
  };

  // ES6
  multiply = (x, y) => { return x * y };

  console.log(multiply(2, 3));

  ```

Arrow functions are quicker to write because they don't require variable assignment. Also, if you're only passing one argument into the arrow function, you don't need to use brackets around the parameter:

  ```js
  multiplyByTen = num => { return 10 * num };

  console.log(multiplyByTen(5));
  ```

If you're only going to `return` a single line in an arrow function, you don't even need the curly brackets (or the `return` keyword):

  ```js
  greet = name => `Hello, I am ${name}!`;

  console.log(greet('Ada Lovelace'));
  ```

However, there are some important differences between arrow functions and ES5 functions aside from syntax. Try the following exercise:

  ```js
  const ourClass = {
    members: ['Raymond', 'Adis', 'Flavia', 'Nabil', 'Kiya'],
    className: 'London Class 2',
    classSummary: function() {
      return this.members.map(function(member) {
        return `${member} is in ${this.className}`;
      });
    }
  };

  console.log(ourClass.classSummary());
  ```

The above code doesn't quite work. We've got an object, the `ourClass` object, and within it, and array, a string and a method. But `this.className` is returning as `undefined` - the code isn't seeing what we're trying to point it to.

Let's try with an arrow function:

  ```js
  const ourClass = {
    members: ['Raymond', 'Adis', 'Flavia', 'Nabil', 'Kia'],
    className: 'London Class 2',
    classSummary: function() {
      return this.members.map((member) => {
        return `${member} is in ${this.className}`;
      });
    }
  };

  console.log(ourClass.classSummary());
  ```

With that one little change, the function is now working. Why? Well, arrow functions differ to ES5 functions in that they make use of something called 'lexical `this`'. JavaScript is a 'lexical' programming language; this means that how the code behaves depends on the order or placement of each piece of code. When we use an arrow function, the value of `this` is bound to the surrounding context. So unlike when we used the anonymous function in the ES5 version(`this.members.map(function(member) {`), the arrow function lets the JavaScript engine know where `this` is pointing to.

If this is confusing, don't worry; we're going to move onto `this` in greater depth shortly. But first, let's do a few exercises with arrow functions.


> **Exercise**:
>
> Use [JSBin](https://jsbin.com/) for today's exercises.
>
> 1. Write an arrow function that returns the string, `Hello, I am ${name}, and I am ${age} years old.`
> 2. Write an arrow function that takes an array of integers, and returns the sum of the elements in the array. Google and use the built-in `reduce` array method for this.
> 3. The syntax of this function is wonky. Can you fix it to use the shortest arrow function possible?
> ```js
>  let eye = "eye";
>
>   const fire =
>  (
>
>  ) =
>  >
>   {
>     return `bulls-`;
>   }
>   ```
> 4. Refactor the following ES5 function to use an arrow function:
> ```js
const fibonacci = function(n) {
  if (n < 3) return 1;
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```