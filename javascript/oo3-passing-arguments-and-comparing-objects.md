# Passing Arguments and Comparing Objects

## Passing a Primitive

- In JavaScript, a primitive (e.g., string, number, boolean, ...) is **immutable.** In other words, any changes made to an argument **inside** a function effectively creates a **copy** local to that function, and does not affect the primitive **outside** of that function.

```javascript
function changeToEight(n) {
  n = 8; // whatever n was, it is now 8... but only in this function!
}

let n = 7;

changeToEight(n);

console.log(n);
// 7
```

## Passing an Object

On the other hand, objects in JavaScript are **mutable**. If you pass an object into a function, Javascript passes a **reference** to that object. Let's see what happens if we pass an object into a function and then modify a property:

```javascript
let originalObject = {
  favoriteColor: 'red'
};

function setToBlue(object) {
  object.favoriteColor = 'blue';
}

setToBlue(originalObject);

originalObject.favoriteColor;
// 'blue'
```

Since objects in JavaScript are passed by reference, if we make changes to that reference, we're actually directly modifying the original object itself.

What's more: the same rule applies when re-assigning an object to a new variable, and then changing that copy. Again, since objects are passed by reference, the original object is changed as well.

```javascript
const iceCreamOriginal = {
  Andrew: 3,
  Richard: 15
};

const iceCreamCopy = iceCreamOriginal;

iceCreamCopy.Richard;
// 15

iceCreamCopy.Richard = 99;

iceCreamCopy.Richard;
// 99

iceCreamOriginal.Richard;
// 99
```

## Comparing Objects

Naturally, one might expect the `parrot` object and `pigeon` object to be equal. After all, both objects look exactly the same.However, the expression will only return `true` when comparing two references to exactly the same object.

```javascript
const parrot = {
  group: 'bird',
  feathers: true,
};

const pigeon = {
  group: 'bird',
  feathers: true,
};

parrot === pigeon;
// false

const myBird = parrot;

myBird === parrot;
// true
```

---
Udacity course: [Object-Oriented JavaScript](https://www.udacity.com/course/object-oriented-javascript--ud711)
