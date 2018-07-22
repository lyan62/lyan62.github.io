---
title: "098 Validate Binary Search Tree"
permalink: /leetcode/tree/098
layout: single
classes: wide
tags: [leetcode, tree, easy]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/validate-binary-search-tree/description/):
> Given a binary tree, determine if it is a valid binary search tree (BST).
> Assume a BST is defined as follows: 
> - The left subtree of a node contains only nodes with keys less than the node's key.  
> - The right subtree of a node contains only nodes with keys greater than the node's key.  
> - Both the left and right subtrees must also be binary search trees.


----------------------------
- 要求： 
给一个binary tree。




--------------------------
- 返回：
判断它是不是一棵BST 

----------------------------

- 例子：
	- input:  
	 2
   / \
 1    3
	- output: True


----------------------------

## Solution
利用stack, 从root 走到最左边节点，并依次将经过的节点加入stack,再依次比较左中右。

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        stack = []
        curr = root
        prev = None
        while curr or stack:
            while curr:
                stack.append(curr)
                curr = curr.left  # 从root走到最左边节点,并保留所经过的节点到stack
				
            if stack:
                curr = stack.pop()
                if prev and curr.val <= prev.val:
                    return False
                prev = curr
                curr = curr.right 
        return True
```