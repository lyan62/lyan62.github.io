---
title: "105 Construct Binary Tree from Preorder and Inorder Traversal"
permalink: /leetcode/tree/105
layout: single
classes: wide
tags: [leetcode, tree, medium]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)  
> Given preorder and inorder traversal of a tree, construct the binary tree.



----------------------------
- 要求： 
给inorder, preorder traversal 的数组，返回对应的树




--------------------------
- 返回：  
对应的树

----------------------------

- 例子：
	- input: preorder = [3,9,20,15,7]， inorder = [9,3,15,20,7]
	- output:   
。    3
。   / \
。  9  20
。。 /  \
。。15   7


----------------------------

## Solution
还是recursive的思想，由于从preorder中可以提取root, 可以使用root在inorder的序列分出左右子树，再对左右子树重复上述过程。

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def buildTree(self, preorder, inorder):
        """
        :type preorder: List[int]
        :type inorder: List[int]
        :rtype: TreeNode
        """
        if len(preorder) == 0:
            return None
        if len(preorder) == 1:
            return TreeNode(preorder[0])
        
        # recursively use root in preorder to separate inorder into left and right subtree
        root = TreeNode(preorder[0])
        root_idx = inorder.index(root.val)
        root.left = self.buildTree(preorder[1 : root_idx + 1], inorder[0 : root_idx])
        root.right = self.buildTree(preorder[root_idx + 1 :], inorder[root_idx + 1 :])
        return root
```