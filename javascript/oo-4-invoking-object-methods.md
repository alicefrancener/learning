# Invoking object methods

## Function vs. Methods

We can extend **functionality** to objects by adding **methods** to them. A **method** is a property of an object whose value is a **function.**

```javascript
const developer = {
  name: 'Andrew'
};

developer.sayHello = function () {
  console.log('Hi there!');
};
```

## Calling Methods

We can access a function in an object using the property name. Just like calling a function, an object's method is called by adding parentheses at the end of the method's name.

```javascript
const developer = {
  name: 'Andrew',
  sayHello: function () {
    console.log('Hi there!');
  }
};

developer.sayHello();
// 'Hi there!'

developer['sayHello']();
// 'Hi there!'
```

## A Method Can Access the Object it was Called On

Using `this`, methods can directly access the object that it is called on.

```javascript
const triangle = {
  type: 'scalene',
  identify: function () {
    console.log(`This is a ${this.type} triangle.`);
  }
};

triangle.identify();
// 'This is a scalene triangle.'
```

When you say `this`, what you're really saying is "*this objec*t" or "*the object at hand*."

Using `this` to change a object property:

```javascript
const chameleon = {
    color: 'green',
    changeColor: function() {
        this.color = 'pink'
    }
};

chameleon.changecolor();
chameleon.color
//pink
```

---

Udacity course: [Object-Oriented JavaScript](https://www.udacity.com/course/object-oriented-javascript--ud711)
["this" in Method]([https://javascript.info/object-methods#this-in-methods](https://javascript.info/object-methods#this-in-methods)
