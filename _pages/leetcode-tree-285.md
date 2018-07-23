---
title: "285 Inorder Successor in BST"
permalink: /leetcode/tree/285
layout: single
classes: wide
tags: [leetcode, tree, medium]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/inorder-successor-in-bst/description/)  
> Given a binary search tree and a node in it, find the in-order successor of that node in the BST.



----------------------------
- 要求： 
给一个binary tree, 和一个节点 p,找出 p 的 inorder successor.


--------------------------
- 返回：  
successor 节点

----------------------------

- 例子：
	- input:  
	root = [2,1,3], p = 1

  2
 / \
1   3

	- output: 2


----------------------------

## Solution
由于 inorder traversal 返回一个有序序列，那么先inorder排序， 通过 p.val确定inorder中p节点的index, 返回第index+1的节点。

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def inorderSuccessor(self, root, p):
        """
        :type root: TreeNode
        :type p: TreeNode
        :rtype: TreeNode
        """

        nodes = self.inOrder(root, [])
        vals = [n.val for n in nodes]
        index = vals.index(p.val)
        if index == len(vals)-1:
            return None
        elif nodes[index+1]:
            return nodes[index+1]

        
    def inOrder(self, root, nodes):
        if root and root.left:
            self.inOrder(root.left, nodes)
        nodes.append(root)
        if root and root.right:
            self.inOrder(root.right, nodes)
        return nodes            
```