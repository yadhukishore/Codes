# 1512. Number of Good Pairs

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var numIdenticalPairs = function(nums) {
    let result=0;
    const hash={};
    for(let val of nums){
        result += hash[val]||0;
        hash[val] = (hash[val]||0)+1;
    }
    return result;
};

```
