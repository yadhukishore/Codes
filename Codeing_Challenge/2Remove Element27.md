# 27. Remove Element
```typescript
function removeElement(nums: number[], val: number): number {
    let k:number = 0;
    for(let i=0;i<nums.length;i++){
        if(nums[i]!==val){
            nums[k]=nums[i];
            k++;
        }
    }
    return k
};
```
### CheckLink:- https://medium.com/@robertsevan/leetcode-problem-27-remove-element-leetcode-top-interview-150-2ccf28875032

## Similar questions


### 1. **Move Zeroes**
   - **Problem:** Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.
   - **Example:**
     - Input: `[0,1,0,3,12]`
     - Output: `[1,3,12,0,0]`
```javascript
function moveZerosToRight(nums){
  let count = 0;
  for(let i = 0; i < nums.length; i++){
    if(nums[i] !== 0){
      nums[count] = nums[i];
      count++;
    }
  }
  for(let i = count; i < nums.length; i++){
    nums[i] = 0;
  }
  return nums;
}
console.log(moveZerosToRight( [0,1,0,3,12]))
```

### 2. **Remove Duplicates from Sorted Array**
   - **Problem:** Given a sorted array `nums`, remove the duplicates in-place such that each element appears only once and return the new length. Do not allocate extra space for another array; you must do this by modifying the input array in-place with O(1) extra memory.
   - **Example:**
     - Input: `[1,1,2]`
     - Output: `2, nums = [1,2,_]`

```typescript
function removeDuplicates(nums: number[]): number {
    if (nums.length === 0) return 0;

    let k = 1; // Initialize k to 1 since the first element is always unique.

    for (let i = 1; i < nums.length; i++) {
        if (nums[i] !== nums[i - 1]) {
            nums[k] = nums[i];
            k++;
        }
    }

    return k;
}

```

### 3. **Two Sum II - Input Array Is Sorted**
   - **Problem:** Given an array of integers `numbers` that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number. Return the indices of the two numbers.
   - **Example:**
     - Input: `numbers = [2,7,11,15]`, `target = 9`
     - Output: `[1,2]`
```typescript
function twoSum(numbers: number[], target: number): number[] {
    let left: number = 0;
    let right: number = numbers.length - 1;

    while (left < right) {
        const sum: number = numbers[left] + numbers[right];

        if (sum === target) {
            return [left + 1, right + 1]; // Return 1-indexed positions
        } else if (sum < target) {
            left++; // Move the left pointer to the right to increase the sum
        } else {
            right--; // Move the right pointer to the left to decrease the sum
        }
    }

    return []; // Return an empty array if no solution is found (though problem guarantees one solution)
}

```
### 4. **Find All Numbers Disappeared in an Array**
   - **Problem:** Given an array of integers where `1 ≤ a[i] ≤ n` (n = size of the array), some elements appear twice and others appear once. Find all the elements of `[1, n]` inclusive that do not appear in this array.
   - **Example:**
     - Input: `[4,3,2,7,8,2,3,1]`
     - Output: `[5,6]`

### 5. **Find the Duplicate Number**
   - **Problem:** Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive, there is only one repeated number in `nums`. Return this repeated number.
   - **Example:**
     - Input: `[1,3,4,2,2]`
     - Output: `2`

