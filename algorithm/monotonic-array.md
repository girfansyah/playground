# Monotonic array

{% hint style="info" %}
a function that takes in an array of integers and returns a boolean representing whether the array is monotonic

&#x20;An array is said to be monotonic if its elements, from left to right, are entirely non-increasing or entirely non-decreasing.&#x20;

\
Non-increasing elements aren't necessarily exclusively decreasing; they simply don't increase. Similarly, non-decreasing elements aren't necessarily exclusively increasing; they simply don't decrease. Note that empty arrays and arrays of one element are monotonic.&#x20;

**Sample input**&#x20;

`array = [-1, -5, -10, -1100, -1100, -1101, -1102, -9001]`&#x20;

**Sample output**&#x20;

`true`
{% endhint %}

```javascript
function isMonotonic(array) {
  let isMonotonic = true;

  for (let i = 1; i < array.length; i++) {
    if (array[i] < array[i - 1] || array[i] > array[i - 1]) {
      isMonotonic = false;
      break;
    }
  }

  return isMonotonic;
}
```
