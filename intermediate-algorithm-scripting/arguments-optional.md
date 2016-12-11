#### Arguments Optional

Create a function that sums two arguments together. If only one argument is provided, then return a function that expects one argument and returns the sum.

For example, `addTogether(2, 3)` should return `5`, and `addTogether(2)` should return a function.

Calling this returned function with a single argument will then return the sum:

`var sumTwoAnd = addTogether(2);`

`sumTwoAnd(3)` returns `5`.

If either argument isn't a valid number, return undefined.

```javascript
function addTogether() {
  // put arguments into array to be able to call array functions on them
  var args = Array.from(arguments);

  return args.some(function(arg) {
    return typeof arg !== 'number'; }) ?
    // return undefined if any of the arguments aren't numbers
    // else check for > 1 arguments
    undefined : args.length > 1 ?
    // if > 1 arguments sum arguments and return the sum
    args.reduce(function(a,b) {
      return a += b; }, 0) :
    // else check if second argument outside of args array
    function(b) { return typeof b === 'number' ?
    // if there is & a number, add it to first sum
    // else, return undefined if it's not a number
      b + args[0] : undefined;
    };
}

addTogether(2)(3);
```
