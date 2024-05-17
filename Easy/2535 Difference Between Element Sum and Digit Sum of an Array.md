```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var differenceOfSum = function(nums) {
    let eleSum = nums.reduce((acc,curr)=>acc+curr)
    let distint = nums.join('').split('');
    let digitSum = distint.reduce((acc,curr)=>parseInt(acc)+parseInt(curr));
    return eleSum-digitSum
};
```
