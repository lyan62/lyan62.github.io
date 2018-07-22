---
title: "102 Binary Tree Level Order Traversal"
permalink: /leetcode/tree/102
layout: single
classes: wide
tags: [leetcode, tree, easy]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---



> [Original Description](https://leetcode.com/problems/binary-tree-level-order-traversal/description/):
> Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level)..  

----------------------------
- 要求： 
给一个binary tree，逐层遍历




--------------------------
- 返回：  
level order traversal

----------------------------

- 例子：
	- input: [3,9,20,null,null,15,7]
	- output:  
	[[3],
	 [9,20],
	 [15,7]]


----------------------------

## Solution
使用dfs,用level记录高度，根节点高度为0。

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        
        res = []
        self.dfs(root, 0, res)
        return res

    def dfs(self, root, depth, res):
        if root == None:
            return res
        if len(res) < depth+1:
            res.append([])
        res[depth].append(root.val)
        self.dfs(root.left, depth+1, res)
        self.dfs(root.right, depth+1, res)
```