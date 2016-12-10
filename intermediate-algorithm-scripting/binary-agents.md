#### Binary Agents

Return an English translated sentence of the passed binary string.

The binary string will be space separated.

```javascript
function binaryAgent(str) {
  // split into each binary 'letter'
  // map over each 'letter and convert from binary (base 2)
  // to the correct character, then rejoin to create a string again!
  return str.split(" ").map(function(letter) {
    return String.fromCharCode(parseInt(letter, 2));
  }).join("");
}

binaryAgent("01000001 01110010 01100101 01101110 00100111 01110100 00100000 01100010 01101111 01101110 01100110 01101001 01110010 01100101 01110011 00100000 01100110 01110101 01101110 00100001 00111111");
```
