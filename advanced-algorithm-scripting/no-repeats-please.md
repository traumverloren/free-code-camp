#### No repeats please

Return the number of total permutations of the provided string that don't have repeated consecutive letters. Assume that all characters in the provided string are each unique.

For example, `aab` should return 2 because it has 6 total permutations (`aab`, `aab`, `aba`, `aba`, `baa`, `baa`), but only 2 of them (`aba` and `aba`) don't have the same letter (in this case a) repeating.

```javascript
// https://en.wikipedia.org/wiki/Heap%27s_algorithm
// Use Heap's Algorithm

/*
procedure generate(n : integer, A : array of any):
    if n = 1 then
          output(A)
    else
        for i := 0; i < n; i += 1 do
            generate(n - 1, A)
            if n is even then
                swap(A[i], A[n-1])
            else
                swap(A[0], A[n-1])
            end if
        end for
        generate(n - 1, A)
    end if
*/

function permAlone(str) {
  let array = str.split("");
  let permutations = [];

  function swap(a,b) {
    let tempValue = array[a];
    array[a] = array[b];
    array[b] = tempValue;
  }

  function generate(n) {
    if (n === 1) {
      permutations.push(array.join(""));
    } else {
      for (var i=0; i < n; i++) {
        generate(n-1);
        if (n % 2 === 0) {
          swap(i, n-1);
        } else {
          swap(0, n-1);
        }
      }
    }
  }

  generate(array.length);

  // regex to find if a char occurs more than 1x.
  let regex = /([a-zA-Z])\1/;

  let filtered = permutations.filter(function(item, pos) {
    return !item.match(regex);
  });

// return # of permutations
return filtered.length;
}

permAlone('aab');
```
