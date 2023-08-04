# Branch sum

{% hint style="info" %}
Write a function that takes in a Binary Search Tree (BST) and a target integer value and returns the closest value to that target value contained in the BST.\


You can assume that there will only be one closest value.

Each BST node has an integer value, a left child node, and a right child node. A node is said to be a valid BST node if and only if it satisfies the BST property: its value is strictly greater than the values of every node to its left; its value is less than or equal to the values of every node to its right; and its children nodes are either valid BST nodes themselves or None / null.\
\
Sample Input

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

Sample Output

```
13
```
{% endhint %}



{% tabs %}
{% tab title="Solution" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
class TreeNode {
  constructor (value, left = null, right = null) {
    this.value = value;
    this.left = left;
    this.right = right;
  }
}

function findClosestValueInBst(tree, target) {
  let closest = tree.value; // Initialize closest to the root value
  let currentNode = tree;

  while (currentNode !== null) {
    if (Math.abs(target - currentNode.value) < Math.abs(target - closest)) {
      closest = currentNode.value;
    }

    if (target < currentNode.value) {
      currentNode = currentNode.left;
    } else if (target > currentNode.value) {
      currentNode = currentNode.right;
    } else {
      // If target is equal to current node's value, no need to search further
      break;
    }
  }

  return closest;
}
```
{% endcode %}

Example usage

```javascript

const bst = new TreeNode(10);
bst.left = new TreeNode(5);
bst.right = new TreeNode(15);
bst.left.left = new TreeNode(2);
bst.left.right = new TreeNode(5);
bst.right.left = new TreeNode(13);
bst.right.right = new TreeNode(22);
bst.left.left.left = new TreeNode(1);
bst.right.left.right = new TreeNode(14);

const target = 12;
const closestValue = findClosestValueInBst(bst, target);
console.log("Closest value:", closestValue); // Output should be 13
```
{% endtab %}
{% endtabs %}
