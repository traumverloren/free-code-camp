#### Convert HTML Entities
Convert the characters `&, <, >, "` (double quote), and `'` (apostrophe), in a string to their corresponding HTML entities.

```javascript
function convertHTML(str) {
  var chars = {"&":"&amp;", "<":"&lt;", ">":"&gt;", "\"":"&quot;", "'":"&apos;"};

  return str.split('').map(function(letter) {
    return chars[letter] || letter;
  }).join('');

}

convertHTML("Hamburgers < Pizza < Tacos");
```
