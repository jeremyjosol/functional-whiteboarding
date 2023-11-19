## Array Deduping

* _Remove duplicates from an array_.
* _Solve without using `.filter()`_.
* _Solve without recursion then with_.

**Edge Cases**: None.

**Example**:

- Input: `[7, 9, “hi”, 12, “hi”, 7, 53]`
- Output: `[7, 9, “hi”, 12, 53]`

> Pseudocode solution without recursion:

Initialize an empty array.
Loop through the input array and inside of our loop, we're going to check if the index of the user input array is equal to the current [index] and using `indexOf()` will check only for the first occurrence, not any subsequent element.

Then we’ll refer back to our empty array and `push()` user input index and outside of the loop, we’ll return the empty array.

----------

> Pseudocode solution with recursion:

Our function will take 3 parameters, the user input array, an index starting at `0` to ‘loop’ over, and an empty array.

Our base case, which will terminate the recursion once its condition is met, will check if the length of the input array is equal to the current index. If it is, meaning each element has been processed, shall return our empty array.

Now for our condition to be met, we check if the empty array does NOT (!) include the index (which will be incremented recursively) of the user input array.

If this case is true, we’ll push the elements of the input array into the unique array. Indicating that as the loop is happening, it’s only pushing elements that has already been included, not those of which are not unique.

Now, outside of these conditions, we can return our function with the same parameters passed in, only difference being that the index is incremented to ‘loop’ through the array.

### Solution

> // without recursion

```javascript
const findUniqueElements = (inputArray) => {
  const uniqueArray = [];

  for (let i = 0; i < inputArray.length; i++) {
    if (i === inputArray.indexOf(inputArray[i])) {
      uniqueArray.push(inputArray[i]);
    }
  }

  return uniqueArray;
}
```

> // with recursion

```javascript
const findUniqueElements = (inputArray, index = 0, uniqueArray = []) => {
  if (index === inputArray.length) {
    return uniqueArray;
  }

  if (!uniqueArray.includes(inputArray[index])) {
    uniqueArray.push(inputArray[index]);
  }
  
  return findUniqueElementsRecursive(inputArray, index + 1, uniqueArray);
}
```