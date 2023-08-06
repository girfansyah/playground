---
description: Converts binary strings to characters - O(n)
---

# Binary Agent

```javascript
/**
 * @param {string} str - Binary strings
 * @returns {string} Converted string characters
 */
module.exports = function binaryAgent(str) {
  if (str === '') return '';

  const binaryCharacters = str.split(' ');
  const convertedCharacters = binaryCharacters.map(character => {
    const charCode = parseInt(character, 2);
    return String.fromCharCode(charCode);
  });

  return convertedCharacters.join('');
};

```
