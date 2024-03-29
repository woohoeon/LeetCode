## Sum of Left Leaves (왼쪽 잎의 합)

Find the sum of all left leaves in a given binary tree.

주어진 이진 트리에서 모든 왼쪽 잎의 합을 찾으십시오.

Example:

```
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.
```

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
var sumOfLeftLeaves = function(root) {
    let sum = 0
    const process = node => {
        if (!node) {
            return
        }
        let leftNum
        if (node.left !== null) {
            if (node.left.left === null && node.left.right === null) {
                leftNum = node.left.val    
            }
            process(node.left)
        }
        if (node.right !== null) {
            process(node.right)
        }
        if (leftNum) {
            sum = sum + leftNum
        }
        
    }
    process(root)
    return sum
};
```
