# Node Depths

{% hint style="info" %}
The distance between a node in a Binary Tree and the tree's root is called the node's depth.&#x20;

\
Write a function that takes in a Binary Tree and returns the sum of its nodes' depths.

&#x20;Each BinaryTree node has an integer value, a left child node, and a right child node. Children nodes can either be BinaryTree nodes themselves or None / null.\
\
**Sample Input**

```javascript
tree =    1
       /     \
      2       3
    /   \   /   \
   4     5 6     7
 /   \
8     9
```

**Sample Output**

```javascript
16
// The depth of the node with value 2 is 1.
// The depth of the node with value 3 is 1.
// The depth of the node with value 4 is 2.
// The depth of the node with value 5 is 2.
// Etc..
// Summing all of these depths yields 16.
```
{% endhint %}

{% tabs %}
{% tab title="Solution" %}
{% code title="binaryTreeDepth.js" overflow="wrap" lineNumbers="true" %}
```javascript
// O(n) time | O(h) space
function nodeDepths(root, depth = 0) {
  if (root === null) return 0;
  return depth + nodeDepths(root.left, depth + 1) + nodeDepths(root.right, depth + 1);
}

// This is the class of the input binary tree.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

exports.nodeDepths = nodeDepths;
```
{% endcode %}

\
**Example usage**

{% code title="main.js" overflow="wrap" lineNumbers="true" %}
```javascript
const { nodeDepths, BinaryTree } = require('./binaryTreeDepth.js');

// Helper function to construct a binary tree
function buildSampleTree() {
  const root = new BinaryTree(1);
  root.left = new BinaryTree(2);
  root.right = new BinaryTree(3);
  root.left.left = new BinaryTree(4);
  root.left.right = new BinaryTree(5);
  root.right.left = new BinaryTree(6);
  root.right.right = new BinaryTree(7);
  root.left.left.left = new BinaryTree(8);
  root.left.left.right = new BinaryTree(9);
  return root;
}

// Sample input
const tree = buildSampleTree();

// Calculate and log the sum of depths of nodes in the binary tree
const sumOfDepths = nodeDepths(tree);
console.log(sumOfDepths); // Output: 16

```
{% endcode %}
{% endtab %}
{% endtabs %}
