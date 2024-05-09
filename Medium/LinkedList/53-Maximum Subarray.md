```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    let Maximum = nums[0];
    let currMax = nums[0];

    for(let i = 1 ; i<nums.length ; i++){
        currMax = Math.max(nums[i],nums[i]+currMax);
        Maximum = Math.max(Maximum,currMax);
    }
    return Maximum;
};

```
