#### Sum All Odd Fibonacci Numbers

Given a positive integer num, return the sum of all odd Fibonacci numbers that are less than or equal to num.

The first two numbers in the Fibonacci sequence are 1 and 1. Every additional number in the sequence is the sum of the two previous numbers. The first six numbers of the Fibonacci sequence are 1, 1, 2, 3, 5 and 8.

For example, `sumFibs(10)` should return 10 because all odd Fibonacci numbers less than 10 are 1, 1, 3, and 5.

My final solution:
```javascript
function sumFibs(num) {
  var fibArr = [1];

  for (var i = 1; i <= num;) {
    fibArr.push(i);
    // add second to last and last number in array to get current i
    i = fibArr[fibArr.length-2] + fibArr[fibArr.length-1];
  }

  // Calculate the result, excluding even nums
  return fibArr.reduce(function(a, b) {
    if (b % 2 !== 0) {
      return a + b;
    } else {
      return a;
    }
  });
}

sumFibs(4);
```

My first solution:
```javascript
function sumFibs(num) {
  var result = 0;
  var currentNum = 1;
  var lastNum = 0;

  while (currentNum <= num) {
    if (currentNum % 2 !== 0) {
      result += currentNum;
    }
    currentNum += lastNum;
    lastNum = currentNum - lastNum;
  }

  return result;
}

sumFibs(4);
```
