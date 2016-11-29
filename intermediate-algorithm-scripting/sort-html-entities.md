#### Convert HTML Entities
Convert the characters `&, <, >, "` (double quote), and `'` (apostrophe), in a string to their corresponding HTML entities.

```javascript
function convertHTML(str) {
  var chars = {"&":"&amp;", "<":"&lt;", ">":"&gt;", "\"":"&quot;", "'":"&apos;"};

  function replaceChars(match) {
    return chars[match];
  }

  return str.split('').map(function(letter) {
    return letter.replace(/[^\w\s]/, replaceChars);
  }).join('');

}

convertHTML("Hamburgers < Pizza < Tacos");
```
