# Find the Closest Value in the Binary tree search

{% hint style="info" %}
**Find the Closest Value in BTS**

Write a function that takes in a Binary Search Tree (BST) and a target integer value and returns the closest value to that target value contained in the BST.

You can assume that there will only be one closest value. Each BST node has an integer value, a left child node, and a right child node. A node is said to be a valid BST node if and only if it satisfies the BST property: its value is strictly greater than the values of every node to its left; its value is less than or equal to the values of every node to its right; and its children nodes are either valid BST nodes themselves or None / null.\
\
**Sample Input**

```javascript
tree =   10
       /     \
      5      15
    /   \   /   \
   2     5 13   22
 /           \
1            14
target = 12

```

**Sample Output**

```
13
```
{% endhint %}



{% tabs %}
{% tab title="Solution" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
class TreeNode {
  constructor (val, left = null, right = null) {
    this.val = val;
    this.left = left;
    this.right = right;
  }
}

function findClosestValueInBST(node, target) {
  let closest = node.val;

  while (node !== null) {
    if (Math.abs(node.val - target) < Math.abs(closest - target)) {
      closest = node.val;
    }

    if (target < node.val) {
      node = node.left;
    } else if (target > node.val) {
      node = node.right;
    } else {
      break;
    }
  }

  return closest;
}
```
{% endcode %}

**Example usage**

```javascript

const tree = new TreeNode(10);
tree.left = new TreeNode(5);
tree.right = new TreeNode(15);
tree.left.left = new TreeNode(2);
tree.left.right = new TreeNode(5);
tree.left.left.left = new TreeNode(1);
tree.right.left = new TreeNode(13);
tree.right.right = new TreeNode(22);
tree.right.left.right = new TreeNode(14);

const target = 12;
const result = findClosestValueInBST(tree, target);
console.log(`Closest value to ${target} in the BST is: ${result}`);
```
{% endtab %}
{% endtabs %}
