---
description: Finds the difference of the elements in two arrays
---

# Different Array

```javascript
/**
 * @param {array} arr1
 * @param {array} arr2
 * @returns {array} diffArr - The array that contains the differing elements
 */
module.exports = function diffArray(arr1, arr2) {
  const combinedSet = new Set([...arr1, ...arr2]);
  const diffArr = [...combinedSet].filter(
    el => !(arr1.includes(el) && arr2.includes(el))
  );

  return diffArr;
};

```
