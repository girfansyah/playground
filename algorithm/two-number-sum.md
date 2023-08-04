# 1⃣ Two number sum

{% hint style="info" %}
Write a function that takes in a non-empty array of distinct integers and an integer representing a target sum. If any two numbers in the input array sum up to the target sum, the function should return them in an array, in any order. If no two numbers sum up to the target sum, the function should return an empty array.

Note that the target sum has to be obtained by summing two different integers in the array; you can't add a single integer to itself in order to obtain the target sum.

You can assume that there will be at most one pair of numbers summing up to the target sum.\


**#Sample Input**

```javascript
// Some code
array = [3, 5, -4, 8, 11, 1, -1, 6]
targetSum = 10
```

**#Sample Output**

```javascript
// Some code
[-1, 11] // the numbers could be in reverse order
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
```javascript
// O(n^2) time | O(1) space

function twoNumberSum(array, targetSum) {
  for (let i = 0; i < array.length - 1; i++) {
    const firstNum = array[i];
    for (let j = i + 1; j < array.length; j++) {
      const secondNum = array[j];
      if (firstNum + secondNum === targetSum) {
        return [firstNum, secondNum];
      }
    }
  }
  return []
}
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

