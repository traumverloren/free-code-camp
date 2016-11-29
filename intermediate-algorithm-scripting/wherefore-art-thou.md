#### Wherefore Art Thou

Make a function that looks through an array of objects (first argument) and returns an array of all objects that have matching property and value pairs (second argument). Each property and value pair of the source object has to be present in the object from the collection if it is to be included in the returned array.

For example, if the first argument is `[{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }]`, and the second argument is { last: "Capulet" }, then you must return the third object from the array (the first argument), because it contains the property and its value, that was passed on as the second argument.

```javascript
function whatIsInAName(collection, source) {

  sourceKeys = Object.keys(source);

  // filter if collection has source keys,
  // returns the object if every criteria is met
  return collection.filter(function(object) {
    console.log(object);
    return sourceKeys.every(function(key) {
      console.log(key);
      console.log(object.hasOwnProperty(key));
      // The every() method tests whether
      // each objects in the array match the
      // source keys, it only returns true based on the
      // criteria below
      return object.hasOwnProperty(key) && object[key] === source[key];
    });
  });
}

whatIsInAName([{ "a": 1, "b": 2 }, { "a": 1 }, { "a": 1, "b": 2, "c": 2 }], { "a": 1, "c": 2 });
```
