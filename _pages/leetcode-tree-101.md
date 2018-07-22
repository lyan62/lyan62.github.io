---
title: "101 Symmetric Tree"
permalink: /leetcode/tree/101
layout: single
classes: wide
tags: [leetcode, tree, easy]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---



> [Original Description](https://leetcode.com/problems/symmetric-tree/description/):
> Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).  

----------------------------
- 要求： 
给一个binary tree, 判断它是不是对称




--------------------------
- 返回：  
True/False

----------------------------

- 例子：
	- input: [1,2,2,3,4,4,3]   
	 1
    / \
   2   2
 / \  / \
3  4  4  3

	- output: True


----------------------------

## Solution
判断根的left & right children是否相等;  
如果相等，判断left.right & right.left, 以及left.left & right.right 是否相等，do this recursively.

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if root:
            return self.help(root.left, root.right)
        return True

    def help(self, p, q):
        if p == None and q == None: return True
        if p and q and p.val == q.val:
            return self.help(p.right, q.left) and self.help(p.left, q.right)
        else:
            return False
```