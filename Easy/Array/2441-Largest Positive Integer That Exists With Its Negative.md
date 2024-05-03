```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxK = function(nums) {
    nums.sort((a,b)=>b-a);
    for(let i=0;i<nums.length;i++){
        const val = nums[i];
        if(val && nums.includes(-val)){
            return val;
        }
    }
    return -1;
};
```
