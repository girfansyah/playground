---
description: Bubble sort algorithm
---

# Bubble sort

```javascript
/**
 * @param {array} numbers
 * @return {array} The sorted array
 */

module.exports = function bubbleSort(numbers) {
  const length = numbers.length;

  for (let i = 0; i < length; i++) {
    let swapped = false;

    for (let j = 0; j < length - i - 1; j++) {
      if (numbers[j] > numbers[j + 1]) {
        [numbers[j], numbers[j + 1]] = [numbers[j + 1], numbers[j]];
        swapped = true;
      }
    }

    if (!swapped) break; //if no swaps, the array is already sorted
  }

  return numbers;
};

```
