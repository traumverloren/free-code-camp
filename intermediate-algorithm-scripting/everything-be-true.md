#### Everything Be True

Check if the predicate (second argument) is truthy on all elements of a collection (first argument).

Remember, you can access object properties through either dot notation or [] notation.

```javascript
function truthCheck(collection, pre) {
  // Is everyone being true?

  function checkForProperty(element) {
    return element[pre];
  }

  return collection.every(checkForProperty);
}

truthCheck([{"user": "Tinky-Winky", "sex": "male"}, {"user": "Dipsy", "sex": "male"}, {"user": "Laa-Laa", "sex": "female"}, {"user": "Po", "sex": "female"}], "sex");
```
