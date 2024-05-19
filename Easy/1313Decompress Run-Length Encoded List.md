```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var decompressRLElist = function(nums) {
    const result=[]
    for(let i=0 ; i<nums.length ; i+=2){
        const freq=nums[i];
        const val = nums[i+1];
        for(let j=0;j<freq;j++){
            result.push(val);
        } 
    }
    return result;
};
```
 - To achieve O(n) time complexity for decompressing the run-length encoded list, we need to avoid nested loops that might cause O(n^2) complexity. The given solution does not actually operate in O(n^2) as it's merely appending elements to an array in a single pass through the input list. Each push operation is O(1), and appending freq times contributes to O(n) complexity in total because freq sums up to the total length of the result array.

```javascript
function decompressRLElist(nums) {
    const result = [];
    for (let i = 0; i < nums.length; i += 2) {
        const freq = nums[i];
        const val = nums[i + 1];
        result.push(...new Array(freq).fill(val));
    }
    return result;
}

// Example usage:
console.log(decompressRLElist([1, 2, 3, 4])); // Output: [2, 4, 4, 4]
console.log(decompressRLElist([1, 1, 2, 3])); // Output: [1, 3, 3]

```
