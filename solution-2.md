## Array Deduping

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