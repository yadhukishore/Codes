# 2331. Evaluate Boolean Binary Tree

To solve the problem of evaluating a Boolean binary tree, we need to understand the structure and evaluation rules of such a tree. Here’s a detailed step-by-step explanation:

### Problem Understanding
1. **Tree Structure**:
   - A **full binary tree** where each node has either 0 or 2 children.
   - **Leaf nodes** have values 0 or 1 (0 represents False, 1 represents True).
   - **Non-leaf nodes** have values 2 or 3 (2 represents the boolean OR operation, 3 represents the boolean AND operation).

2. **Evaluation Rules**:
   - If a node is a leaf, its evaluation is its value (True or False).
   - If a node is a non-leaf, evaluate its two children first. Then apply the boolean operation represented by the node’s value (2 for OR, 3 for AND) to the results of the evaluations of its children.

### Example Breakdown
**Example 1**:
- Input: `[2, 1, 3, null, null, 0, 1]`
- Tree Representation:
  ```
      2
     / \
    1   3
       / \
      0   1
  ```
- Evaluation Process:
  1. Evaluate leaf nodes:
     - Leaf node with value 1 evaluates to True.
     - Leaf node with value 0 evaluates to False.
     - Leaf node with value 1 evaluates to True.
  2. Evaluate non-leaf nodes:
     - Node with value 3 (AND) with children 0 and 1 evaluates to False AND True = False.
     - Node with value 2 (OR) with children 1 and (result of node 3) evaluates to True OR False = True.
  3. The root node evaluates to True, so the output is `true`.

**Example 2**:
- Input: `[0]`
- The tree has a single leaf node with value 0, which evaluates to False.
- Output: `false`.

### Constraints
- The number of nodes is between 1 and 1000.
- Nodes values are constrained to 0, 1 (for leaves) and 2, 3 (for non-leaves).


```javascript
/**
0 -> False
1 -> True
2 -> OR
3 -> AND
*/

// Depth First Search 
var evaluateTree = function (root) {
  const dfs = (node) => {
    if (!node) return;
    if (node.val === 0) return false;
    if (node.val === 1) return true;

    if (node.val === 2) {
      return dfs(node.left) || dfs(node.right);
    } else if (node.val === 3) {
      return dfs(node.left) && dfs(node.right);
    }
  };

  return dfs(root);
};
```
## Working:-
 *Let's go through the provided JavaScript implementation of the `evaluateTree` function, which uses Depth First Search (DFS) to evaluate a Boolean binary tree.*

### Code Explanation

#### Function Signature and Helper Function
```javascript
var evaluateTree = function (root) {
  const dfs = (node) => {
    // ... implementation details
  };

  return dfs(root);
};
```
- `evaluateTree` is the main function that starts the evaluation of the tree.
- Inside `evaluateTree`, a helper function `dfs` is defined. This function performs a Depth First Search on the tree to evaluate it.

#### Helper Function Logic
```javascript
const dfs = (node) => {
  if (!node) return;
  if (node.val === 0) return false;
  if (node.val === 1) return true;

  if (node.val === 2) {
    return dfs(node.left) || dfs(node.right);
  } else if (node.val === 3) {
    return dfs(node.left) && dfs(node.right);
  }
};
```
- **Base Case**:
  - `if (!node) return;`: If the current node is `null`, simply return. This is a guard clause and not typically encountered due to the full binary tree structure guarantee.
  - `if (node.val === 0) return false;`: If the node value is `0`, it represents `False`. Return `false`.
  - `if (node.val === 1) return true;`: If the node value is `1`, it represents `True`. Return `true`.

- **Recursive Case**:
  - `if (node.val === 2)`: If the node value is `2`, it represents the `OR` operation.
    - `return dfs(node.left) || dfs(node.right);`: Recursively evaluate the left and right children and return the logical OR of their evaluations.
  - `else if (node.val === 3)`: If the node value is `3`, it represents the `AND` operation.
    - `return dfs(node.left) && dfs(node.right);`: Recursively evaluate the left and right children and return the logical AND of their evaluations.

#### Execution
```javascript
return dfs(root);
```
- The main function `evaluateTree` invokes the `dfs` function starting from the `root` of the tree and returns the result.

### Step-by-Step Example

Let's walk through an example to see how the function works in practice.

#### Example Tree
```
      2
     / \
    1   3
       / \
      0   1
```
- Represented as an array: `[2, 1, 3, null, null, 0, 1]`

#### Execution Steps
1. `evaluateTree(root)` is called with the root node having value `2`.
2. `dfs(root)` is called with the root node.
3. Since the root node value is `2`, the function performs:
   - `dfs(node.left)` with node value `1` which returns `true` (because `1` represents `True`).
   - `dfs(node.right)` with node value `3`.
4. For the right child (node value `3`):
   - `dfs(node.left)` with node value `0` returns `false` (because `0` represents `False`).
   - `dfs(node.right)` with node value `1` returns `true`.
   - The logical AND of these results is `false && true` which is `false`.
5. The logical OR of the root's left and right child evaluations is `true || false` which is `true`.

Thus, the final output is `true`.

### Summary
The implementation uses a depth-first search strategy to evaluate the binary tree recursively:
- Leaf nodes return their boolean values directly.
- Non-leaf nodes apply the appropriate boolean operation (`OR` for `2` and `AND` for `3`) to the results of their child nodes' evaluations.

This approach ensures that the tree is evaluated correctly according to the defined boolean operations and values.
