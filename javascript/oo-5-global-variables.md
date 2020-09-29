# Global variables

The `lookAround()` code is a method because it belongs to an object. Since it's a method, it's invoked as a property on the `chameleon` object:

```jsx
const chameleon = {
  eyes: 2,
  lookAround: function () {
     console.log(`I see you with my ${this.eyes} eyes!`);
  }
};

chameleon.lookAround();
```

`whoThis()` is not a method; it's a plain, old, regular function.

```jsx
function whoThis () {
  this.trickyish = true
}

whoThis();
```

**How the function is invoked determines the value of `this` inside the function.**

When a regular function is invoked, the value of `this` is the global **window** object.

***The `window` Object**I*

*f you haven't worked with the `window` object yet, this object is provided by the browser environment and is globally accessible to your JavaScript code using the identifier, `window`. This object is not part of the JavaScript specification (i.e., ECMAScript); instead, it is developed by the [W3C](https://www.w3.org/Consortium/).*

*This `window` object has access to a ton of information about the page itself, including:*

- *The page's URL (`window.location;`)*
- *The vertical scroll position of the page (`window.scrollY'`)*
- *Scrolling to a new location (`window.scroll(0, window.scrollY + 200);` to scroll 200 pixels down from the current location)*
- *Opening a new web page (`window.open("https://www.udacity.com/");`)*

## **Global Variables are Properties on `window`**

Since the `window` object is at the highest (i.e., global) level, an interesting thing happens with global variable declarations. Every variable declaration that is made at the global level (outside of a function) automatically becomes a property on the `window` object!

### ***Globals and `var`, `let`, and `const`***

*The keywords `var`, `let`, and `const` are used to declare variables in JavaScript. `var` has been around since the beginning of the language, while `let` and `const` are significantly newer additions (added in ES6).*

*Only declaring variables with the `var` keyword will add them to the `window` object. If you declare a variable outside of a function with either `let` or `const`, it will not be added as a property to the `window` object.*

## **Global Functions are Methods on `window`**

Similarly to how global variables are accessible as properties on the `window` object, any global function declarations are accessible on the `window` object as methods:

```jsx
function learnSomethingNew() {
  window.open('https://www.udacity.com/');
}

window.learnSomethingNew === learnSomethingNew
// true
```

## **Avoid Globals**

Global variables and functions are *not* ideal. There are actually a number of reasons why, but the two we'll look at are:

- **Tight coupling**: use to indicate code that is too dependent on the details of each other. In tight coupling, pieces of code are joined together in a way where changing one unintentionally alters the functioning of some other code.
- **Name collisions:** occurs when two (or more) functions depend on a variable with the same name. A major problem with this is that both functions will try to update the variable and or set the variable, but these changes are overridden by each other.

So what should you do instead? You should write as few global variables as possible. Write your variables inside of the functions that need them, keeping them as close to where they are needed as possible.

---

Udacity course: [Object-Oriented JavaScript](https://www.udacity.com/course/object-oriented-javascript--ud711)
