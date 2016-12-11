#### Arguments Optional

Create a function that sums two arguments together. If only one argument is provided, then return a function that expects one argument and returns the sum.

For example, `addTogether(2, 3)` should return `5`, and `addTogether(2)` should return a function.

Calling this returned function with a single argument will then return the sum:

`var sumTwoAnd = addTogether(2);`

`sumTwoAnd(3)` returns `5`.

If either argument isn't a valid number, return undefined.

```javascript
function addTogether() {
  var args = Array.from(arguments);

  // check that 2 arguments and all args are numbers
  return args.some(function(arg) {
    return typeof arg !== 'number'; }) ?
    undefined : args.length > 1 ?
    args.reduce(function(a,b) {
      return a += b; }, 0) :
    function(b) { return typeof b === 'number' ?
      b + args[0] : undefined;
    };
}

addTogether(2)(3);
```
