---
description: >-
  Drop the elements of an array (first argument), starting from the front, until
  the predicate (second argument) returns true
---

# Drop elements

```javascript
/**
 * @param {array} arr - The input array
 * @param {function} func - The function used to test elements
 * @returns {array} remainingArr - The array with remaining elements
 */
module.exports = function dropElements(arr, func) {
  while (arr.length > 0 && !func(arr[0])) {
    arr.shift();
  }

  return arr;
};

```
