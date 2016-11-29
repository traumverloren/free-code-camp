#### Convert HTML Entities
Convert the characters `&, <, >, "` (double quote), and `'` (apostrophe), in a string to their corresponding HTML entities.

My second solution:
```javascript
function convertHTML(str) {
  var chars = {"&":"&amp;", "<":"&lt;", ">":"&gt;", "\"":"&quot;", "'":"&apos;"};

  function replaceChars(match) {
    return chars[match];
  }

  return str.replace(/([^\w\s])/g, replaceChars);

}

convertHTML("Hamburgers < Pizza < Tacos");
```

My first solution:
```javascript
function convertHTML(str) {
  var chars = {"&":"&amp;", "<":"&lt;", ">":"&gt;", "\"":"&quot;", "'":"&apos;"};

  return str.split('').map(function(letter) {
    return chars[letter] || letter;
  }).join('');

}

convertHTML("Hamburgers < Pizza < Tacos");
```
