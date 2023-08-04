# Non-Constructible Change

{% hint style="info" %}
**Sample Input**

```javascript
[5, 7, 1, 1, 2, 3, 22]
```

**Sample Output**

```javascript
20
```
{% endhint %}

{% tabs %}
{% tab title="Solution" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
function nonConstructibleChange(coins) {
    coins.sort((a, b) => a - b); // Sort the coin denominations in ascending order
    
    let minChange = 0;
    
    for (const coin of coins) {
        if (coin > minChange + 1) {
            return minChange + 1;
        }
        minChange += coin;
    }
    
    return minChange + 1;
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
