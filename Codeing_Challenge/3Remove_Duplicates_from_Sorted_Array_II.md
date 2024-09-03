#  80.Remove Duplicates from Sorted Array II

```typescript
function removeDuplicates(nums: number[]): number {
    let k: number = 0;

    for (let i = 0; i < nums.length; i++) {
        if (k < 2 || nums[i] > nums[k - 2]) {
            nums[k] = nums[i];
            k++;
        }
    }

    return k;
}
```

### Explanation

- **k < 2:** This allows the first two elements to be added without any checks, ensuring that at least two instances of any number can exist.
- **nums[i] > nums[k - 2]:** This condition checks whether the current element is different from the element at position `k-2`. If it is, then it means adding `nums[i]` to the array will keep the count of that element at most two.



### Time Complexity
- **O(n)** where `n` is the length of the array. The algorithm only makes a single pass through the array.

### Space Complexity
- **O(1)** extra space, as the algorithm modifies the array in-place.


## Similarly,What if it allows the first three elements to be added without any checks

```typescript

function removeDuplicates(nums: number[]): number {
    let k: number = 0;

    for (let i = 0; i < nums.length; i++) {
        if (k < 3 || nums[i] > nums[k - 3]) {
            nums[k] = nums[i];
            k++;
        }
    }

    return k;
}

```
