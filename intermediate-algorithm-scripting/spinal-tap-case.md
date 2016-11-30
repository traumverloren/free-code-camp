#### Spinal Tap Case

Convert a string to spinal case. Spinal case is all-lowercase-words-joined-by-dashes.

```javascript
function spinalCase(str) {

  // if there is capital next to lower case, add a space first.
  str = str.replace(/([a-z])([A-Z])/g, '$1 $2');

  function replaceSpace(match) {
    return '-';
  }

  // finally lowercase string and replace whitespace and underscores with dashes
  return str.toLowerCase().replace(/([\s_])/g, replaceSpace);
}

spinalCase('ThisIsSpinalTap');
```
