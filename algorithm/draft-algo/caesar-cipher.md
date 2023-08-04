# Caesar cipher

{% code title="caesar-cipher.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = class CaesarCipher {
  constructor(shift) {
    this.shift = shift;
    this.UPPERCASE_A = 65;
    this.UPPERCASE_Z = 90;
  }

  /**
   * Translates char codes and join string
   * @param {array} charCodes An array of char codes
   * @returns {string} The translated string
   */
  translateCharCode(charCodes) {
    return String.fromCharCode(...charCodes);
  }

  /**
   * Encodes or decodes string based on the mode
   * @param {string} str String to be encoded or decoded
   * @param {number} mode Encoding (1) or decoding (-1) mode
   * @returns {string} The encoded or decoded string
   */
  transformString(str, mode) {
    const capStr = str.toUpperCase();
    const characters = [];

    for (let i = 0; i < capStr.length; i++) {
      const currentChar = capStr.charCodeAt(i);
      const isValidCharCodeRange =
        currentChar >= this.UPPERCASE_A && currentChar <= this.UPPERCASE_Z;

      if (isValidCharCodeRange) {
        let transformedChar = currentChar + mode * this.shift;

        if (mode === 1) {
          if (transformedChar > this.UPPERCASE_Z)
            transformedChar = transformedChar - this.UPPERCASE_Z + this.UPPERCASE_A - 1;
        } else {
          if (transformedChar < this.UPPERCASE_A)
            transformedChar = this.UPPERCASE_Z - (this.UPPERCASE_A - transformedChar) + 1;
        }

        characters.push(transformedChar);
      } else {
        characters.push(currentChar);
      }
    }

    return this.translateCharCode(characters);
  }

  /**
   * Encodes string
   * @param {string} str String to be encoded
   * @returns {string} The encoded string
   */
  encode(str) {
    return this.transformString(str, 1);
  }

  /**
   * Decodes string
   * @param {string} str String to be decoded
   * @returns {string} The decoded string
   */
  decode(str) {
    return this.transformString(str, -1);
  }
};
```
{% endcode %}

**Example usage**

```javascript
const CaesarCipher = require('./caesar-cipher.js');

/**
Create an instance of the CaesarCipher class by providing the shift value
**/

const shiftValue = 3; // Replace with the desired shift value
const cipher = new CaesarCipher(shiftValue);

/**
Use the encode and decode methods to transform strings:
**/
const originalString = "HELLO WORLD";

// Encode the string
const encodedString = cipher.encode(originalString);
console.log('Encoded:', encodedString);

// Decode the encoded string
const decodedString = cipher.decode(encodedString);
console.log('Decoded:', decodedString);


```
