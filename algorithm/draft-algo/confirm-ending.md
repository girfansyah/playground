---
description: Checks if the string ends with the target string
---

# Confirm ending

```javascript
/**
 * @param {string} str
 * @param {string} target
 * @return {boolean} Whether the string ends with the target string.
 */
module.exports = function confirmEnding(str, target) {
  const cleanStr = str.replace(/[^A-Za-z0-9]/g, '');
  return cleanStr.endsWith(target);
};

```
