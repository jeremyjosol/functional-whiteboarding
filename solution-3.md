## Compressing Strings

* _Takes a string with repeated characters_.
* _‘Compresses’ them, using a number to show how many times a repeated character was compressed_.

**Edge Cases**: None?

**Example**:

- Input: `"aaa"`
- Output: `"3a"`

> Pseudocode solution:

We'll need a variable to hold the final result. 
<br />
Initialize a variable containing an empty string.
<br />
Initialize a counter which wouldn’t need to start at `0` because the string will only show how many occurrences greater than `1`, not `0` occurrences.

`compressedString = ‘’;`

`count = 1;`

Loop through the user input, check to see if the index of the user input is equal to the user input `index + 1`. If true, increment counter.

Now, we need to check if our counter is greater than `1`.
If our counter is greater than `1`, we’ll append the count to the `compressedString` variable.

If array looks like this: `[a, a, b, b, c]`
Then our `compressedString` would currently look something like this: `compressedString = 22`

So, we need to append the user input index to the `compressedString` the same way we did with the counter to display the remaining characters.

Once we’ve done that, we can simply return our `compressedString` which given the case of the array that we set above, should look like this:
`compressedString = 2a2b1c`

----------

### Solution

> without recursion

```javascript
function compressString(inputArray) {
  if (inputArray.length === 0) {
    return '';
  }

  let compressedString = '';
  let count = 1;

  for (let i = 0; i < inputArray.length; i++) {
    if (inputArray[i] === inputArray[i + 1]) {
      count++;
    } else {
      if (count > 1) {
        compressedString += count;
      }
      compressedString += inputArray[i];
      count = 1;
    }
  }

  return compressedString;
}
```

> with recursion 

```javascript
const compressString = (inputArray, index = 0, compressedString = '', count = 1) => {
  if (index === inputArray.length) {
    if (count > 1) {
      compressedString += count;
    }
    return compressedString;
  }

  if (inputArray[index] === inputArray[index + 1]) {
    count++;
  } else {
    if (count > 1) {
      compressedString += count;
    }
    compressedString += inputArray[index];
    count = 1;
  }

  return compressStringRecursive(inputArray, index + 1, compressedString, count);
}

```