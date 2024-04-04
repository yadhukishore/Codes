```javascript

/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var countPairs = function (nums, target) {
    let i = 0;
    let j = 1;
    let count = 0;
    let n = nums.length - 1
    while (i < n) {
        if (nums[i] + nums[j] < target) {
            count++
        }
        if (j == n) {
            i++;
            j = i;
        }
        j++
    }
    return count
};

```
