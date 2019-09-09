## Minimum Distance Between BST Nodes (BST 노드 사이의 최소 거리)

Given a Binary Search Tree (BST) with the root node root, return the minimum difference between the values of any two different nodes in the tree.

루트 노드 루트가있는 BST (Binary Search Tree)가 주어지면 트리에있는 두 개의 다른 노드 값 사이의 최소 차이를 반환하십시오.

Example :

```
Input: root = [4,2,6,1,3,null,null]
Output: 1
Explanation:
Note that root is a TreeNode object, not an array.

The given tree [4,2,6,1,3,null,null] is represented by the following diagram:

          4
        /   \
      2      6
     / \    
    1   3  

while the minimum difference in this tree is 1, it occurs between node 1 and node 2, also between node 3 and node 2.
```

Note:

The size of the BST will be between 2 and 100.
The BST is always valid, each node's value is an integer, and each node's value is different.

Solution: 

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var minDiffInBST = function(root) {
    const arr = [];
    const addArray = (node) => {
        if (node.val !== null) {
            arr.push(node.val)
        }
        if (node.left !== null) {
            addArray(node.left)
        }
        if (node.right !== null) {
            addArray(node.right)
        }
    }
    addArray(root)
    let min
    arr.some((val, index) => {
        if (min === 1) {
            return true
        }
        arr.map((other, otherIndex) => {
            if (index !== otherIndex) {
                const result = Math.abs(val - other)
                min = min ? result < min ? result : min : result
            }
        })
        return false
    })
    return min
};
```
