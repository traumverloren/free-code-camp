#### Pairwise

Given an array `arr`, find element pairs whose sum equal the second argument `arg` and return the sum of their indices.

If multiple pairs are possible that have the same numeric elements but different indices, return the smallest sum of indices. Once an element has been used, it cannot be reused to pair with another.

For example `pairwise([7, 9, 11, 13, 15], 20)` returns `6`. The pairs that sum to 20 are `[7, 13]`` and `[9, 11]``. We can then write out the array with their indices and values.

Index |	0 |	1 |	2 | 3 | 4
------|
Value |	7 |	9	| 11 | 13	| 15

Below we'll take their corresponding indices and add them.

7 + 13 = 20 → Indices 0 + 3 = 3

9 + 11 = 20 → Indices 1 + 2 = 3

3 + 3 = 6 → Return `6`

```javascript
function pairwise(arr, arg) {
  // let's not change the original array, make a copy...
  let sampleArr = [...arr];

  return sampleArr.reduce((acc, curr, index) => {
    // other number are we looking for
    const numberNeeded = arg - curr;

    // if numberNeeded isn't found in sampleArr
    // or numberNeeded ==== curr, ignore     
    if (sampleArr.indexOf(numberNeeded) !== -1 && sampleArr.indexOf(numberNeeded) !== index) {

      const numIndex = sampleArr.indexOf(numberNeeded);
      const sum = numIndex + index;

      sampleArr.splice(index, 1, undefined);
      sampleArr.splice(numIndex, 1, undefined);

      // add sum of matched indexes to the running accumulated total
      return acc + sum;
    }

    // just return the accumulated total if conditions not met
    return acc;
  }, 0);
}

pairwise([0, 0, 0, 0, 1, 1], 1);
```
