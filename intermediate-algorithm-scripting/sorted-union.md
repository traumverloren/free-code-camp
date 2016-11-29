#### Sorted Union
Write a function that takes two or more arrays and returns a new array of unique values in the order of the original provided arrays.

In other words, all values present from all arrays should be included in their original order, but with no duplicates in the final array.

The unique numbers should be sorted by their original order, but the final array should not be sorted in numerical order.

```javascript
function uniteUnique(arr) {
  var array = Array.from(arguments).reduce(function(a, b) {
    return a.concat(b);
  }, []);

  return array.reduce(function(a, b) {
    if (a.indexOf(b) === -1) {
      a.push(b);
    }
    return a;
  }, []);


}
uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);

```
