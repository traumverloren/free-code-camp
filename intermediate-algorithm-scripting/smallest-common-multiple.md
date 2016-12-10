#### Smallest Common Multiple
Find the smallest common multiple of the provided parameters that can be evenly divided by both, as well as by all sequential numbers in the range between these parameters.

The range will be an array of two numbers that will not necessarily be in numerical order.

e.g. for 1 and 3 - find the smallest common multiple of both 1 and 3 that is evenly divisible by all numbers between 1 and 3.

```javascript
function smallestCommons(arr) {
  var startNum = Math.min(arr[0], arr[1]);
  var endNum = Math.max(arr[0], arr[1]);
  var range = [];

  // create array of all numbers from startNum to endNum
  for (var i = endNum; i >= startNum; i--) {
    range.push(i);
  }

  // euclidean greatest common denominator
  // https://en.wikipedia.org/wiki/Euclidean_algorithm
  function gcd(a, b) {
    return !b ? a : gcd(b, a % b);
  }

  // euclidean least common multiple
  // https://en.wikipedia.org/wiki/Least_common_multiple
  function lcm(a, b) {
    return (a * b) / gcd(a, b);   
  }

  // cycle thru the array and find the smallest common multiple
  // using euclid's lcm algorithm
  var multiple = startNum;
  range.forEach(function(n) {
    multiple = lcm(multiple, n);
  });

  return multiple;  
}


smallestCommons([13,1]);
```
