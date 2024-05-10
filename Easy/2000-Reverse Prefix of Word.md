```javascript
/**
 * @param {string} word
 * @param {character} ch
 * @return {string}
 */
var reversePrefix = function(word, ch) {
    const index = word.indexOf(ch);
    if (index < 0 || word === ch) return word;

    // Reverse the prefix part of the word up to the index (inclusive)
    const prefix = word.slice(0, index + 1);
    const reversedPrefix = prefix.split('').reverse().join('');

    // Concatenate the reversed prefix with the remaining part of the word
    const remaining = word.slice(index + 1);
    return reversedPrefix + remaining;
};
```
