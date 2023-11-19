## Checking for Uniqueness

* _Check if all elements in a string are unique_.
  * > meaning all characters in the string are different.
* Return bool.

**Examples**: 

- Input: `“hello”`
- Output: `false`

- Input: `“copyright”`
- Output: `true`

**Edge cases**:
Cannot convert into an array.

> Pseudocode solution

We need to start by looping through the user input array to examine each element.

For each element, we need to begin an inner loop, starting from i + 1, to compare the current element with subsequent elements, this is what will help us check for duplicate elements.
        
Now, for each element at index `j`, where `j` is greater than `i`, we need to check if `userInput[i]` is equal to `userInput[j]`.

If so, it means there are duplicate elements, so we return false.

After completing both loops and not finding any duplicate elements, return true.

### Solution

```javascript
const isUnique = (userInput) => {
	for (let i = 0; i < userInput.length; i++) {
		for (let j = i + 1; j < userInput.length; j++) {
			if (userInput[i] === userInput[j]) {
				return false;
			}
		}
	}
	return true;
}
```
		
