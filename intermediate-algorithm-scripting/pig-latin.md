#### Pig Latin

Translate the provided string to pig latin.

Pig Latin takes the first consonant (or consonant cluster) of an English word, moves it to the end of the word and suffixes an "ay".

If a word begins with a vowel you just add "way" to the end.

Input strings are guaranteed to be English words in all lowercase.

```javascript
function translatePigLatin(str) {
  var vowels = ["a", "e", "i", "o", "u"];

  function findVowel(letter) {
    if (vowels.indexOf(str.charAt(letter)) === -1) {
      return findVowel(letter + 1);
    } else {
      return letter;
    }
  }

  return str.substr(findVowel(0)).concat(findVowel(0) === 0 ? 'way' : str.substr(0, findVowel(0)) + 'ay');

}

// my first crappy solution:
// var vowels = ["a", "e", "i", "o", "u"];
//   var newStr = str;

//   for (var letter in str) {
//     if (vowels.includes(str[0])) {
//       return newStr.concat("way");
//     } else if (!vowels.includes(str[letter])) {
//       console.log(str[letter]);
//        newStr = newStr.substr(1) + newStr.substr(0, 1);
//     } else {
//        return newStr.concat("ay");
//     }
//   }  

//   return newStr;
// }

translatePigLatin("california");
```
