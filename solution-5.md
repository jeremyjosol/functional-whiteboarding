## Array Sorting

* _Sort an array_. 
* _Research different sort methods_.
* _Opt for quickSort._

**Edge cases**:
Can't use `.sort()`

**Example**:

- Input: `[9, 2, 7, 12]`

- Output: `[2, 7, 9, 12]`

> Pseudocode solution 

First, we'll check if the length of the input array is less than or equal to 1, if that is the case, we'll simply return the array.

Now we need to choose the first element of the user input array as `main` for comparison.

We'll also need to initialize two arrays to store elements, an element that is less than the main and one greater.

So we'll need to declare 3 variables:

`const main = inputArray[0]`

`const lessThan = []`

`const greaterThan = []`

With our variables in place, we'll go ahead and loop through the user input array starting from index `1`.
If the current element is less than the `main`, push it to the `lessThan` array, otherwise, push it to the `greaterThan` array.

Then, we'll recursively apply the quickSort method to the `lessThan` array and concatenate the result with the `main` and the result of quickSort on the `greaterThan` array and return our sorted array.

```javascript

const quickSort = function(array) => {
  if (array.length <= 1) {
    return array;
  }

  const main = array[0];
  const lessThan = [];
  const greaterThan = [];

  for (let i = 1; i < array.length; i++) {
    if (array[i] < main) {
      lessThan.push(array[i]);
    } else {
      greaterThan.push(array[i]);
    }
  }

  return quickSort(lessThan).concat(main, quickSort(greaterThan));
}
```