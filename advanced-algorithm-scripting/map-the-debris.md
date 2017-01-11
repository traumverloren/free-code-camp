#### Map the Debris
Return a new array that transforms the element's average altitude into their orbital periods.

The array will contain objects in the format {name: 'name', avgAlt: avgAlt}.

You can read about orbital periods on wikipedia.

The values should be rounded to the nearest whole number. The body being orbited is Earth.

The radius of the earth is 6367.4447 kilometers, and the GM value of earth is 398600.4418 km3s-2.

```javascript
function orbitalPeriod(arr) {
  const GM = 398600.4418;
  const earthRadius = 6367.4447;

  return arr.map(element => {
    const name = element.name;
    const avgAlt = element.avgAlt;
    const r = earthRadius + avgAlt;

    let orbitalPeriod = 2 * Math.PI * Math.sqrt(Math.pow(r, 3)/GM);
    orbitalPeriod = Math.round(orbitalPeriod);

    return {name, orbitalPeriod};
    });
  }

orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]);
```
