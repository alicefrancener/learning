# Create and modify properties

## Creating Objects

To create a new object, you can use:

```javascript
// Using literal notation:
const myObject = {};

// Using the Object() constructor function:
const myObject = new Object();
```

## Modifying Properties

```javascript
const cat = {
  age: 2,
  name: 'Bailey',
  meow: function () {
    console.log('Meow!');
  },
  greet: function (name) {
    console.log(`Hello ${name}`);
  }
};
```

```javascript
cat.age += 1;
cat.age;
// 3

cat.name = 'Bambi';
cat.name;
// 'Bambi'
```

## Adding Properties

Properties can be added to objects simply by specifying the property name, then giving it a value.

```javascript
const printer = {};

printer.on = true;
printer.mode = 'black and white';
printer['remainingSheets'] = 168;
printer.print = function () {
  console.log('The printer is printing!');
};
```

## Removing Properties

```javascript
delete printer.mode;
// true
```

---
Udacity course: [Object-Oriented JavaScript](https://www.udacity.com/course/object-oriented-javascript--ud711)
