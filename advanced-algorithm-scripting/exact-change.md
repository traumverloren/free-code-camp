#### Exact Change
Design a cash register drawer function `checkCashRegister()` that accepts purchase price as the first argument (`price`), payment as the second argument (`cash`), and cash-in-drawer (`cid`) as the third argument.

`cid` is a 2D array listing available currency.

Return the string `"Insufficient Funds"` if cash-in-drawer is less than the change due. Return the string `"Closed"` if cash-in-drawer is equal to the change due.

Otherwise, return change in coin and bills, sorted in highest to lowest order.

```javascript
// omg what a doozy. I did peek at some tips
// to figure this out using an object and reduce.
// I didn't wanna do a switch function
// and a bunch of loops.

function checkCashRegister(price, cash, cid) {
  // create a currency object so can use it
  // to easily associate money name and value.
  // need to order high to low.
  const currency = [
    {name: 'HUNDRED', value: 100},
    {name: 'TWENTY', value: 20},
    {name: 'TEN', value: 10},
    {name: 'FIVE', value: 5},
    {name: 'ONE', value: 1},
    {name: 'QUARTER', value: 0.25},  
    {name: 'DIME', value: 0.1},
    {name: 'NICKEL', value: 0.05},
    {name: 'PENNY', value: 0.01},  
  ];

  let change = cash - price;

  // create a cash in drawer object and sum all monies into a total.
  let drawerMoney = cid.reduce(function(accumulator, current) {
    accumulator.total += current[1];
    accumulator[current[0]] = current[1];

    return accumulator;

  }, {total: 0});
  // moneyz total is total amount in the CID summed together

  // handle insufficient funds cases
  if (drawerMoney.total < change) {
    return "Insufficient Funds";
  }

  // handle when drawer money equal change needed
  if (drawerMoney.total === change) {
    return "Closed";
  }

  // start deducting from cid
  let changeArray = currency.reduce(function(accumulator, current) {
    let valueUsed = 0;
    // while there is still money of this type in the drawer
    // And while the change needed is > currency value...
    while (drawerMoney[current.name] > 0 && change >= current.value) {
      // deduct currency value from change needed
      change -= current.value;
      change = Math.round(change * 100) / 100;
      // deduct currency value from drawerMoney of that type
      drawerMoney[current.name] -= current.value;
      // add this to change left
      valueUsed += current.value;
    }

    // if the currency has been used in the drawer,
    // add it to change array to return
    if (valueUsed > 0) {
      accumulator.push([current.name, valueUsed]);
    }

    return accumulator;  
  }, []);

  // if still change left, then not enough money in drawer!
  if (change > 0) {
    return "Insufficient Funds";
  }

  // Here is your change, ma'am.
  return changeArray;
}

checkCashRegister(3.26, 100.00, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.10], ["QUARTER", 4.25], ["ONE", 90.00], ["FIVE", 55.00], ["TEN", 20.00], ["TWENTY", 60.00], ["ONE HUNDRED", 100.00]]);
```
