
---
title: "104 Maximum Depth of Binary Tree"
permalink: /leetcode/tree/104
layout: single
classes: wide
tags: [leetcode, tree, easy]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---



> [Original Description](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/):
> Given a binary tree, find its maximum depth. The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node. Note: A leaf is a node with no children.


----------------------------
- 要求： 
给一个binary tree。




--------------------------
- 返回：
求其深度

----------------------------

- 例子：
	- input: Given binary tree [3,9,20,null,null,15,7]  
	- output: 3


----------------------------

## Solution
递归得求出左右子树的深度，选择其中较大的。

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        # https://www.cnblogs.com/zuoyuan/p/3782275.html
        if root == None:
            return 0
        else:
            return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
        
```