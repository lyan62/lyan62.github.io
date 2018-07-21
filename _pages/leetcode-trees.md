---
permalink: /leetcode/tree/
layout: single
classes: wide
title: "Binary Trees"
tags: [leetcode, tree, easy]
date:   2018-07-21
sidebar:
  nav: "leetcode"
---



## Definition
![a binary tree](https://i.imgur.com/gWhpTr4.jpg src="https://coderbyte.com/algorithm/tree-traversal-algorithms")

```python
class Node:
  def __init__(self, data):
    self.data = data
    self.left = None
    self.right = None
    
# create nodes
root = Node('A')
n1 = Node('B')
n2 = Node('C')
n3 = Node('D')
n4 = Node('E')

# setup children
root.left = n1
root.right = n2
n1.left = n3
n1.right = n4
```
( example and code src: [codebyte](https://coderbyte.com/algorithm/tree-traversal-algorithms))

- **depth** of node n: number of nodes on the search path from root to n, not including n itself.
- **height** of the tree: maximum depth of any node in the tree.

- **full binary tree**: all nodes other than leaves has two children
- **perfect binary tree**: every parent has two children
	- number of nodes in a perfect binary tree of height $$h$$:  $$2^{h+1}-1$$
	- number of leaves: $$2^{h}$$	 

## Tree traversal
**Binary search trees**: left.data <  root.data < right.data 
- **inorder**: allows data arranged in order.
left --> root --> right (左根右)
- **preorder**: 
root --> left --> right （根左右）
- **postorder**: 
left --> right --> root （左右根）
- **level order**: read level by level

Say we have binary tree of $$n$$ nodes, height $$h$$, for traversals: 
- time complexity = $$O(n)$$;
- space complexity = $$O(h)$$.   
(Note: If each node has parent field, traversal can be done with space complexity $$O(1)$$).

### Inorder traversal
```python
def in_order(root, nodes):
    if root and root.left:     #inorder left subtree
        in_order(root.left, nodes)
    nodes.append(root.data)    #root
    if root and root.right:    #inorder right subtree
        in_order(root.right, nodes)
    return nodes

print in_order(root, []) # => ['D', 'B', 'E', 'A', 'C']
```

### Preorder traversal
```python
def pre_order(root, nodes):
    nodes.append(root.data)
    if root and root.left:
        pre_order(root.left, nodes)
    if root and root.right:
        pre_order(root.right, nodes)
    return nodes
print pre_order(root, []) # => ['A', 'B', 'D', 'E', 'C']
```

### Postorder traversal
```python
def post_order(root, nodes):
    if root and root.left:
        post_order(root.left, nodes)
    if root and root.right:
        post_order(root.right, nodes)
    nodes.append(root.data)  
    return nodes

print post_order(root, []) # => ['D', 'E', 'B', 'C', 'A']
```


Basically in the three blocks of codes, only ```nodes.append(root.data)``` changes its position.

### Level order
```python
def level_order(root, nodes):
    queue = [root]
    while queue:
        n = queue.pop(0)
        nodes.append(n.data)
        if n.left:
            queue.append(n.left)
        if n.right:
            queue.append(n.right)
    return nodes

print level_order(root, []) # => ['A', 'B', 'C', 'D', 'E']
```
利用一个queue, 首先将root加入queue, 之后每次从queue中pop出一个将其左右子加入queue序列，将其data加入输出。

## Tricks
- Use recursive algorithm.

