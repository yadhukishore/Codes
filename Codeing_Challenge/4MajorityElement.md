### Moore Voting Algorithm - Step-by-Step Explanation


1. **Initialization**:
   - Start with two variables: `el` and `count`.
   - Set `el` to `None` or any arbitrary value, and set `count` to `0`.

2. **`el` Selection**:
   - Traverse through the array, and for each element:
     - If `count` is `0`, update the `el` to the current element.
     - If the current element is the same as the `el`, increment `count`.
     - If the current element is different from the `el`, decrement `count`.

3. **Final Step**:
   - After completing the traversal, the `el` will be the majority element.



The Moore Voting Algorithm is highly efficient with a time complexity of O(n) and space complexity of O(1), making it an excellent choice for these types of problems.

# Code
```javascript []
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
let el;    
let count = 0;
for(let i=0 ; i<nums.length ; i++){
if(count === 0){
    count=1;
    el=nums[i];
}
else if(nums[i] === el){
    count++;
}
else{
    count--;
}
}
return el;
};
```

