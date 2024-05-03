

```javascript
/**
 * @param {string} word
 * @return {boolean}
 */
var detectCapitalUse = function(word) {
    // Check if all letters are uppercase
    if (word.toUpperCase() === word) {
        return true;
    }
    // Check if all letters are lowercase
    else if (word.toLowerCase() === word) {
        return true;
    }
    // Check if only the first letter is uppercase
    else if (word[0] === word[0].toUpperCase() && word.slice(1).toLowerCase() === word.slice(1)) {
        return true;
    }
    // If none of the conditions are met, return false
    else {
        return false;
    }
};
```

In the third condition, `word[0] === word[0].toUpperCase()` checks if the first character of the string is uppercase. Then, `word.slice(1).toLowerCase() === word.slice(1)` checks if the rest of the string (starting from the second character) is in lowercase.

