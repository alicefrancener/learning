# Questions

- [Questions](#questions)
    - [What is the difference between the equality operator (==) and the strict equality operator (===)?](#what-is-the-difference-between-the-equality-operator--and-the-strict-equality-operator-)
  - [Array methods](#array-methods)
    - [Add an item to the end of an Array: push](#add-an-item-to-the-end-of-an-array-push)
    - [Remove an item from the end of an Array: pop](#remove-an-item-from-the-end-of-an-array-pop)

### What is the difference between the equality operator (==) and the strict equality operator (===)?
- Triple equals (===) checks for strict equality, which means both the type and value must be the same. Double equals (==) on the other hand first performs type coercion so that both operands are of the same type and then applies strict comparison.
- Links: [30 seconds of interviews], [MDN Strict equality (===)], [MDN Equality (==)]

[30 seconds of interviews]: https://30secondsofinterviews.org/
[MDN Strict equality (===)]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality
[MDN Equality (==)]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Equality


## Array methods
### Add an item to the end of an Array: push

The push() method adds one or more elements to the end of an array and returns the new length of the array.
### Remove an item from the end of an Array: pop

Removes the last element from an array and returns that element (`undefined` if the array is empty). This method changes the length of the array.