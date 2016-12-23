#### Inventory Update

Compare and update the inventory stored in a 2D array against a second 2D array of a fresh delivery. Update the current existing inventory item quantities (in `arr1`). If an item cannot be found, add the new item and quantity into the inventory array. The returned inventory array should be in alphabetical order by item.

```javascript
function updateInventory(arr1, arr2) {
  let combinedArr = arr1;

  // combine inventory arrays and update qty if already present
  // in array 1.
  arr2.forEach(item2 => {
    let occurrenceCount = 0;
    arr1.forEach((item1, index) => {
      if (item1[1] === item2[1]) {
        combinedArr[index][0] += item2[0];
        occurrenceCount = 1;
      }
    });
    if (occurrenceCount === 0) {
      combinedArr.push(item2);
    }
  });

  // sort final array
  combinedArr.sort((a,b) => {
    // a gets assigned lower index than b, thus a before b
    if (a[1] < b[1]) {
      return -1;
    }
    // a gets assigned higher index than b, thus a after b
    if (a[1] > b[1]) {
      return 1;
    }
    return 0;
   });

  return combinedArr;
}

// Example inventory lists
var curInv = [
    [21, "Bowling Ball"],
    [2, "Dirty Sock"],
    [1, "Hair Pin"],
    [5, "Microphone"]
];

var newInv = [
    [2, "Hair Pin"],
    [3, "Half-Eaten Apple"],
    [67, "Bowling Ball"],
    [7, "Toothpaste"]
];

updateInventory([[0, "Bowling Ball"], [0, "Dirty Sock"], [0, "Hair Pin"], [0, "Microphone"]], [[1, "Hair Pin"], [1, "Half-Eaten Apple"], [1, "Bowling Ball"], [1, "Toothpaste"]]);
```
