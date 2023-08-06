# Closest Pair

{% hint style="info" %}
Write a function that takes in two non-empty arrays of integers, finds the pair of numbers (one from each array) whose absolute difference is closest to zero, and returns an array containing these two numbers, with the number from the first array in the first position.&#x20;

Note that the absolute difference of two integers is the distance between them on the real number line. For example, the absolute difference of -5 and 5 is 10, and the absolute difference of -5 and -4 is 1.&#x20;

You can assume that there will only be one pair of numbers with the smallest difference.\
\
**Sample input**

```javascript
arrayOne = [-1, 5, 10, 20, 28, 3];
arrayTwo = [26, 134, 135, 15, 17];
```

**Sample output**

```javascript
[28, 26]
```
{% endhint %}



```javascript
function closestPair(arrayOne, arrayTwo) {
  arrayOne.sort((a, b) => a - b);
  arrayTwo.sort((a, b) => a - b);

  let idxOne = 0;
  let idxTwo = 0;
  let minDiff = Infinity;
  let result = [];

  while (idxOne < arrayOne.length && idxTwo < arrayTwo.length) {
    const diff = Math.abs(arrayOne[idxOne] - arrayTwo[idxTwo]);
    if (diff < minDiff) {
      minDiff = diff;
      result = [arrayOne[idxOne], arrayTwo[idxTwo]];
    }

    if (arrayOne[idxOne] < arrayTwo[idxTwo]) {
      idxOne++;
    } else {
      idxTwo++;
    }
  }

  return result;
}
```
