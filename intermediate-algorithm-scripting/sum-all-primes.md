#### Sum All Primes

Sum all the prime numbers up to and including the provided number.

A prime number is defined as a number greater than one and having only two divisors, one and itself. For example, 2 is a prime number because it's only divisible by one and two.

The provided number may not be a prime.

```javascript
function sumPrimes(num) {
  var numbers = [];

  for (var i = 2; i <= num; i++) {
    if (isPrime(i)) {
      numbers.push(i);
      console.log(numbers);
    }
  }

  return numbers.reduce(function(a,b) {
    return a + b;
  });

  // An integer is prime if it is not divisible
  // by any prime less than or equal to its square root
  function isPrime (i) {
    var sqrt = Math.floor(Math.sqrt(i));

    for (var n = 2; n <= sqrt; n++)
    {
        if (i % n === 0)
        {
            return false;
        }
    }
    return true;
  }
}

sumPrimes(10);
```
