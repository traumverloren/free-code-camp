#### Roman Numeral Converter

Convert the given number into a roman numeral.

All roman numerals answers should be provided in upper-case.

```javascript
function convertToRoman(num) {
  var romanNumeral = "";

  var romanNumeralKeys = {M:1000,CM:900,D:500,CD:400,C:100,XC:90,L:50,XL:40,X:10,IX:9,V:5,IV:4,I:1};

  for (i in romanNumeralKeys) {
    while (num >= romanNumeralKeys[i]) {
      romanNumeral += i;
      num -= romanNumeralKeys[i];
    }
  }    

  return romanNumeral;
}

convertToRoman(2);
```
