# Algorithims

## Find the Symmetric Difference

The mathematical term symmetric difference (△ or ⊕) of two sets is the set of elements which are in either of the two sets but not in both. For example, for sets A = {1, 2, 3} and B = {2, 3, 4}, A △ B = {1, 4}.

Symmetric difference is a binary operation, which means it operates on only two elements. So to evaluate an expression involving symmetric differences among three elements (A △ B △ C), you must complete one operation at a time. Thus, for sets A and B above, and C = {2, 3}, A △ B △ C = (A △ B) △ C = {1, 4} △ {2, 3} = {1, 2, 3, 4}.

Create a function that takes two or more arrays and returns an array of their symmetric difference. The returned array must contain only unique values (no duplicates).

### Solutions

- solution 1

```
function sym(args) {
  const arrays = [];
  for (let i = 0; i < arguments.length; i++) {
    arrays.push(arguments[i])
  }

  //console.log("ARRAYS: ", arrays);

  const findDifference = (firstArray, secondArray) => {
    const diff = [];

    firstArray.forEach((item) => {
      if (!secondArray.includes(item) && !diff.includes(item)) {
        diff.push(item)
      }
    });

    secondArray.forEach((item) => {
      if (!firstArray.includes(item) && !diff.includes(item)) {
        diff.push(item)
      }
    });

    return diff;
  };

  const symetricDiff = arrays.reduce(findDifference)
  //console.log("SYMETRIC DIFF: ", symetricDiff);
  return symetricDiff;
}

sym([1, 2, 3], [5, 2, 1, 4]);
```

- solution 2

```
function sym(...args) {
  const difference = args.reduce((uniqueSet, currentArray) => {
    const compareWith = new Set(currentArray);

    for(let item of compareWith) {
      if (uniqueSet.has(item)) uniqueSet.delete(item)
      else {
        uniqueSet.add(item)
      }
    }

    return uniqueSet
  }, new Set())

  const symetricDiff = [...difference];
  return symetricDiff;
}

sym([1, 2, 3], [5, 2, 1, 4]);
```
