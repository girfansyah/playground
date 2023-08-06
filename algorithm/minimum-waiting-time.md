# Minimum waiting time

{% hint style="info" %}
You're given a non-empty array of positive integers representing the amounts of time that specific queries take to execute. Only one query can be executed at a time, but the queries can be executed in any order.\
\
A query's waiting time is defined as the amount of time that it must wait before its execution starts. In other words, if a query is executed second, then its waiting time is the duration of the first query; if a query is executed third, then its waiting time is the sum of the durations of the first two queries.\
\
Write a function that returns the minimum amount of total waiting time for all of the queries. For example, if you're given the queries of durations \[1, 4, 5], then the total waiting time if the queries were executed in the order of \[5, 1, 4] would be (0) + (5) + (5 + 1) = 11. The first query of duration 5 would be executed immediately, so its waiting time would be 0, the second query of duration 1 would have to wait 5 seconds (the duration of the first query) to be executed, and the last query would have to wait the duration of the first two queries before being executed.\
\
**Note**: you're allowed to mutate the input array.\


**Sample `Input`**

`queries = [3, 2, 1, 2, 6]`

\
**Sample Output**\
`17`
{% endhint %}



{% tabs %}
{% tab title="Solution 1" %}
```javascript
function minimumWaitingTime(queries) {
  queries.sort((a, b) => a - b);

  let totalWaitingTime = 0;
  for (let i = 0; i < queries.length; i++) {
    totalWaitingTime += queries[i] * (queries.length - (i + 1));
  }

  return totalWaitingTime;
}
```
{% endtab %}

{% tab title="Solution 2" %}
```javascript
function minimumWaitingTime(queries) {
  queries.sort((a, b) => a - b);

  const totalWaitingTime = queries.reduce((total, duration, index) => {
    const remainingQueries = queries.length - (index + 1);
    return total + duration * remainingQueries;
  }, 0);

  return totalWaitingTime;
}

```
{% endtab %}
{% endtabs %}
