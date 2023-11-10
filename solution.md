## Turning Strings to URLs

* _URLs cannot have spaces_. 
* _Spaces are replaced with `%20`_.
* _Solve with and without recursion_.

**Edge cases**: None really. String input that can either have spaces or no spaces. Can contain letters, numbers, and special characters.

**Example**:

- Input: `"Jasmine Ann Jones"`
- Output `"Jasmine%20Ann%20Jones"`

### Solution

> without recursion

```javascript
const conversion = (userInput) => {
  const url = "";
  for (let i = 0; i < userInput.length; i++) {
    if (userInput[i] === ' ') {
      url += '%20';
    } else {
      url += userInput[i];
    }
  }
  return url;
}
```

> with recursion
```javascript
const conversion = (userInput, index = 0, url = '') => {
  if (userInput.length === index) {
    return url;
  }

  if (userInput[index] === ' ') {
    url += '%20';
  } else {
    url += userInput[index];
  }
  return conversion(userInput, index + 1, url);
}
```

