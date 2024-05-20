```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var validPalindrome = function(s) {
    let left=0;
    let right=s.length-1;
    while(left<right){
        if(s[left]===s[right]){
            left++;
            right--;
        }else{
            return isPalliandrome(s,left+1,right) ||
            isPalliandrome(s,left,right-1);
        }
    }
    return true;
};
function isPalliandrome(s,left,right){
    while(left<right){
        if(s[left]===s[right]){
            left++;
            right--;
        }else{
            return false;
        }
    
    }
    return true;
}
```
