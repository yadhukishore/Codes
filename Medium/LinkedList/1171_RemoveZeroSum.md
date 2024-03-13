# 1171. Remove Zero Sum Consecutive Nodes from Linked List

Given the head of a linked list, we repeatedly delete consecutive sequences of nodes that sum to 0 until there are no such sequences.

After doing so, return the head of the final linked list.  You may return any such answer.

Example 1:

Input: head = [1,2,-3,3,1]

Output: [3,1]

Note: The answer [1,2,1] would also be accepted.

Example 2:


Input: head = [1,2,3,-3,4]

Output: [1,2,4]

Example 3:

Input: head = [1,2,3,-3,-2]

Output: [1]


```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
class ListNode {
    constructor(val) {
        this.val = val;
        this.next = null;
    }
}

var removeZeroSumSublists = function(head) {
    let dummy = new ListNode(0);
    dummy.next = head;
    let current = dummy;
    let sum = 0;
    let map = new Map();

    // First pass: Calculate cumulative sums and save the last occurrence of each sum.
    while (current) {
        sum += current.val;
        map.set(sum, current);
        current = current.next;
    }

    // Reset current to the dummy head for the second pass.
    current = dummy;
    sum = 0;

    // Second pass: Remove zero-sum sublists.
    while (current) {
        sum += current.val;
        // If we have seen this sum before, it means the sublist between the previous occurrence and this one sums to zero.
        current.next = map.get(sum).next;
        current = current.next;
    }

    return dummy.next;
};

```
 

This code aims to remove consecutive sequences of nodes from a linked list where the sum of values in each sequence equals zero. Let's break down the code step by step:


The line `let dummy = new ListNode(0);` creates a dummy node with a value of `0`. This dummy node serves as a placeholder and helps simplify the code, particularly in cases where the removal of nodes starts from the beginning of the list.

Then, `dummy.next = head;` sets the `next` pointer of the dummy node to point to the head of the original linked list. By doing this, the dummy node becomes the new head of the list, and the original head becomes the second node in the list.





1. **ListNode Definition**: This is a simple definition of a node in a singly linked list. Each node has a value (`val`) and a pointer to the next node (`next`).

2. **Function Definition**: `removeZeroSumSublists` is a function that takes the head of a linked list as its argument and returns the head of the modified list.

3. **Initializing Variables**:
   - `dummy`: A dummy node is created to handle cases where the sequence of nodes to be removed starts from the very beginning of the list.
   - `current`: A pointer initialized to `dummy`, which is used to iterate through the linked list.
   - `sum`: A variable to keep track of the cumulative sum of node values encountered while traversing the list.
   - `map`: A map data structure (JavaScript's `Map`) to store the last occurrence of each cumulative sum encountered.

4. **First Pass**:
   - The code iterates through the linked list, updating the cumulative sum as it goes.
   - For each cumulative sum encountered, it saves the last node with that sum into the map.

5. **Second Pass**:
   - The code iterates through the linked list again, resetting the `current` pointer to `dummy`.
   - It calculates the cumulative sum again as it traverses the list.
   - If a cumulative sum is found that was encountered before (i.e., exists in the map), it means there's a sequence of nodes with a sum of zero between the last occurrence of that sum and the current node.
   - In this case, it adjusts the `next` pointer of the previous node to skip over the zero-sum sequence.
   - This effectively removes the zero-sum sequence from the linked list.

6. **Return**:
   - Finally, it returns the `next` pointer of the dummy node, which points to the head of the modified linked list.

Overall, this algorithm efficiently removes consecutive zero-sum sequences from the linked list in two passes, utilizing a dummy node and a map to keep track of cumulative sums and their last occurrences.
