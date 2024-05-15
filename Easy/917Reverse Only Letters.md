## 917. Reverse Only Letters
```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseOnlyLetters = function (s) {
    s = s.split('');
    let start = 0;
    let end = s.length - 1;
    let regex = /[a-zA-Z]/;
    while (start < end) {
        if (regex.test(s[start])) {
            if (regex.test(s[end])) {
                [s[start], s[end]] = [s[end], s[start]]
                start++;
                end--;
            } else {
                end--;
            }
        } else {
            start++;
        }
    }
    return s.join('');
};
```
