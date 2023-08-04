# Sorted squared array

{% hint style="info" %}
**Sample Input**

```
array = [1, 2, 3, 5, 6, 8, 9]
```

**Sample Ourput**

```
[1, 4, 9, 25, 36, 64, 81]
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
```javascript
// O(nlogn) time | O(n) space

function sortedSquaredArray(array) {
  const sortedSquares = new Array(array.length).fill(0);

  for (let i = 0; i < array.length; i++) {
    const element = array[i];
    sortedSquares[i] = element * element;
  }

  sortedSquares.sort((a, b) => a - b); // Sort the sortedSquares array
  return sortedSquares;
}

console.log(sortedSquaredArray([1, 2, 3, 5, 6, 8, 9]));

```
{% endtab %}
{% endtabs %}
