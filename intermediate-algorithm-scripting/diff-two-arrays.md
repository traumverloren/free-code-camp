#### Diff Two Arrays

Compare two arrays and return a new array with any items only found in one of the two given arrays, but not both. In other words, return the symmetric difference of the two arrays.

```javascript
function diffArray(arr1, arr2) {
  var newArr = arr1.concat(arr2);

  //   filter() calls a provided callback function once for each element in an
  //  array, and constructs a new array of all the values for which callback 
  //  returns a value that coerces to true

  return newArr.filter(function (i) {
    return newArr.indexOf(i) === newArr.lastIndexOf(i);  
  });
}

diffArray([1, 2, 3, 5], [1, 2, 3, 4, 5]);
```
