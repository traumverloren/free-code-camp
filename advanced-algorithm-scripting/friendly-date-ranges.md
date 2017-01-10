#### Friendly Date Ranges

Convert a date range consisting of two dates formatted as `YYYY-MM-DD` into a more readable format.

The friendly display should use month names instead of numbers and ordinal dates instead of cardinal (`1st` instead of `1`).

Do not display information that is redundant or that can be inferred by the user: if the date range ends in less than a year from when it begins, do not display the ending year.

Additionally, if the date range begins in the current year (i.e. it is currently the year 2016) and ends within one year, the year should not be displayed at the beginning of the friendly range.

If the range ends in the same month that it begins, do not display the ending year or month.

Examples:

`makeFriendlyDates(["2016-07-01", "2016-07-04"]) should return ["July 1st","4th"]`

`makeFriendlyDates(["2016-07-01", "2018-07-04"]) should return ["July 1st, 2016", "July 4th, 2018"]`.

```javascript
// OMG I'm sooo not proud of this. what a fuckin cluster. Sorry?

function makeFriendlyDates(arr) {

  const monthNames = ["January", "February", "March", "April", "May", "June",
    "July", "August", "September", "October", "November", "December"
  ];

  function formatYear(date) {
    year = date.getFullYear();
    return year;
  }

  function formatMonth(date) {
    month = monthNames[date.getMonth()];
    return month;
  }

  function formatDay(date) {
    day = date.getDate();
    switch (day) {
      case 1:
      case 21:
      case 31:
        return day + 'st';
      case 2:
      case 22:
        return day + 'nd';
      case 3:
      case 23:
        return day + 'rd';
      default:
        return day + 'th';
    }
  }

  function formatDates(arr) {
    const date1 = arr[0];
    const date2 = arr[1];

    const oneDay = 1000*60*60*24;
    const date1_ms = date1.getTime();
    const date2_ms = date2.getTime();
    const dateDiff = Math.round((date2_ms - date1_ms)/oneDay);
    // this has to be wrong for the challenge to pass
    const currentYear = 2016;

    if (date1.getFullYear() === date2.getFullYear()) {
      // begins/ends in the same month
      if (date1.getDate() === date2.getDate()) {
        return [`${formatMonth(date1)} ${formatDay(date1)}, ${formatYear(date1)}`];
      // begins/ends in the same year
      } else if (date1.getMonth() === date2.getMonth()) {
        return [`${formatMonth(date1)} ${formatDay(date1)}`, `${formatDay(date2)}`];
            // begins/ends in the same month
      } else {
        return [`${formatMonth(date1)} ${formatDay(date1)}, ${formatYear(date1)}`, `${formatMonth(date2)} ${formatDay(date2)}`];
      }
    } else if (dateDiff < 365) {
      if (currentYear === date1.getFullYear()) {
        return [`${formatMonth(date1)} ${formatDay(date1)}`, `${formatMonth(date2)} ${formatDay(date2)}`];
      }
      else {
        return [`${formatMonth(date1)} ${formatDay(date1)}, ${formatYear(date1)}`, `${formatMonth(date2)} ${formatDay(date2)}`];
      }
    } else {
      // If dates are > 12 months apart.
      return arr.map(date => {
        return `${formatMonth(date)} ${formatDay(date)}, ${formatYear(date)}`;
      });
    }
 }

  arr = arr.map(date => new Date(date));
  return formatDates(arr);
}

makeFriendlyDates(["2018-01-13", "2018-01-13"]);
```
