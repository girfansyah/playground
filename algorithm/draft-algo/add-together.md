# Add Together

```javascript
/**
 * Adds up a variable number of arguments.
 * @param {...number} args - Numbers to be added
 * @return {(number|function)} The sum of the values or a function to add more values
 */
module.exports = function addTogether(...args) {
  const sum = args.reduce((acc, curr) => {
    if (typeof curr !== 'number') return undefined;
    return acc + curr;
  }, 0);

  if (!sum) return undefined;

  if (args.length > 1) return sum;

  return function addToSum(...moreArgs) {
    const moreSum = moreArgs.reduce((acc, curr) => {
      if (typeof curr !== 'number') return undefined;
      return acc + curr;
    }, 0);

    if (!moreSum) return undefined;

    return moreSum + sum;
  };
};

```
