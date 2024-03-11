# 88. Merge Sorted Array

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.

Example 1:

Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3

Output: [1,2,2,3,5,6]

Example 2:

Input: nums1 = [1], m = 1, nums2 = [], n = 0

Output: [1]

To solve the "Merge Sorted Array" problem using the merge sort algorithm in JavaScript, we need to follow a slightly different approach since the problem statement specifies that we should merge two sorted arrays into one, with the result stored in the first array (`nums1`). The merge sort algorithm is typically used for sorting an array, not for merging two sorted arrays. However, we can adapt the merge process from the merge sort algorithm to solve this problem.

Here's a step-by-step guide to solving this problem:

1. **Understand the Problem**: We are given two sorted arrays (`nums1` and `nums2`) and we need to merge them into `nums1` in a sorted order. The first `m` elements of `nums1` are the ones to be merged, and the last `n` elements are set to 0 and should be ignored.

2. **Algorithm**:
   - Start from the end of both arrays.
   - Compare the last elements of both arrays.
   - Place the larger element at the end of `nums1`.
   - Move the index of the array from which the element was taken one step back.
   - Repeat the process until all elements from `nums2` are placed in `nums1`.

3. **Implementation**:

```javascript
function merge(nums1, m, nums2, n) {
    let i = m - 1; // Index for nums1
    let j = n - 1; // Index for nums2
    let k = m + n - 1; // Index for the last element of nums1

    // Move elements of nums2[0..n-1] to nums1[m..m+n-1]
    while (j >= 0) {
        if (i >= 0 && nums1[i] > nums2[j]) {
            nums1[k] = nums1[i];
            i--;
        } else {
            nums1[k] = nums2[j];
            j--;
        }
        k--;
    }
}
```

4. **Example Usage**:

```javascript
let nums1 = [1,2,3,0,0,0];
let m = 3;
let nums2 = [2,5,6];
let n = 3;

merge(nums1, m, nums2, n);

console.log(nums1); // Output: [1,2,2,3,5,6]
```

This solution works in O(m+n) time complexity, which is optimal for this problem since we need to look at every element in both arrays at least once. The space complexity is O(1) because we are modifying `nums1` in place and not using any additional space.

