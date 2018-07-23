---
title: "230 Kth Smallest Element in a BST"
permalink: /leetcode/tree/230
layout: single
classes: wide
tags: [leetcode, tree, medium]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---



> [Original Description](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/)  
> Given a binary search tree, write a function kthSmallest to find the kth smallest element in it. Note: You may assume k is always valid, 1 ≤ k ≤ BST's total elements.



----------------------------
- 要求： 
给一个binary tree, 找出从小到大的第 k 个值。


--------------------------
- 返回：  
第k个值

----------------------------

- 例子：
	- input:  
	root = [3,1,4,null,2], k = 1

	- output: 1


----------------------------

## Solution
由于 inorder traversal 返回一个有序序列，那么先inorder排序， 再返回该序列中第 k 个节点。

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def kthSmallest(self, root, k):
        """
        :type root: TreeNode
        :type k: int
        :rtype: int
        """
        nodes = self.inOrder(root, [])
        return nodes[k-1].val
        
    def inOrder(self, root, nodes):
        if root and root.left:
            self.inOrder(root.left, nodes)
        nodes.append(root)
        if root and root.right:
            self.inOrder(root.right, nodes)
        return nodes
            
```