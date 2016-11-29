#### Missing letters
Find the missing letter in the passed letter range and return it.

If all letters are present in the range, return undefined.

```javascript
function fearNotLetter(str) {
  for (var i = 0; i < str.length; i++) {
    var ascii = str.charCodeAt(i);

    if (ascii !== str.charCodeAt(0) + i) {
       return String.fromCharCode(str.charCodeAt(0) + i);
    }
  }  
  return undefined;
}

fearNotLetter("abce");
```
