#### Steamroller

Flatten a nested array. You must account for varying levels of nesting.

```javascript
function steamrollArray(arr) {
  // recursion!
  // use reduce to concat array elements
  // if toFlatten element is NOT an array, it concats.
  // if toFlatten element IS an array, we call the steamrollArray on it to flatten the nested arrays!
  return arr.reduce(function(flat, toFlatten) {
    return flat.concat(Array.isArray(toFlatten) ? steamrollArray(toFlatten) : toFlatten);
  }, []);
}

steamrollArray([1, [2], [3, [[4]]]]);
```
