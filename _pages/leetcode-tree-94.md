---
title: "094 Binary Tree Inorder Traversal"
permalink: /leetcode/tree/094
layout: single
classes: wide
tags: [leetcode, tree, medium]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)  
> Given a binary tree, return the inorder traversal of its nodes' values..



----------------------------
- 要求： 
给一个binary tree， inorder traversal.




--------------------------
- 返回：  
inorder的数组

----------------------------

- 例子：
	- input: [1,null,2,3]
	- output: [1,3,2] 


----------------------------

## Solution
Straight forward in-order traversal using recursive.

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        return self.inorder(root, [])
    
    def inorder(self, root, nodes):
        if root and root.left:
            self.inorder(root.left,nodes)
        if root:
            nodes.append(root.val)
        if root and root.right:
            self.inorder(root.right, nodes)
        return nodes
		
	### solution 2:
		# stack = []
        # curr = root
        # result = []
        # while curr or stack:
        #     while curr:
        #         stack.append(curr)
        #         curr = curr.left
        #     if stack:
        #         curr = stack.pop()
        #         result.append(curr.val)
        #         curr = curr.right
        # return result
```