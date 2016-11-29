#### Sum All Numbers in a Range
We'll pass you an array of two numbers. Return the sum of those two numbers and all numbers between them.

The lowest number will not always come first.
```javascript
function sumAll(arr) {
  var minNumber = Math.min.apply(null,arr);
  var maxNumber = Math.max.apply(null,arr);
  var sum = 0;

  for (var i = minNumber; i <= maxNumber; i++) {
    sum += i;
  }

  return sum;  
}

sumAll([1, 4]);

```
