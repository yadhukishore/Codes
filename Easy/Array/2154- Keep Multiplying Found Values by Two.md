To solve this problem, you can use a loop to iterate through the `nums` array and check if the `original` value is present. If it is present, you multiply `original` by 2 and continue the loop with the new value of `original`. If `original` is not found in the array, you return the current value of `original`. Here's the solution:

```javascript
/**
 * @param {number[]} nums
 * @param {number} original
 * @return {number}
 */
var findFinalValue = function(nums, original) {
    while (nums.includes(original)) {
        original *= 2;
    }
    return original;
};
```

Here's how the code works:

1. We start a `while` loop that continues until `original` is not found in the `nums` array.
2. Inside the loop, we multiply `original` by 2 using `original *= 2`.
3. If `original` is not found in `nums` array, the loop terminates, and we return the current value of `original`.

This solution has a time complexity of O(n), where n is the length of the `nums` array, because in the worst case, we might need to iterate through the entire array for each value of `original`.

Here's an example of how the code works for the first example:

```javascript
const nums = [5, 3, 6, 1, 12];
const original = 3;

// Initial call
findFinalValue(nums, original); // Returns 24

// Step-by-step execution
// Loop 1: original = 3, nums.includes(3) => true, original *= 2 => original = 6
// Loop 2: original = 6, nums.includes(6) => true, original *= 2 => original = 12
// Loop 3: original = 12, nums.includes(12) => true, original *= 2 => original = 24
// Loop 4: original = 24, nums.includes(24) => false, return original = 24
```
