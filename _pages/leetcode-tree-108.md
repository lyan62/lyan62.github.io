---
title: "108 Convert Sorted Array to Binary Search Tree"
permalink: /leetcode/tree/108
layout: single
classes: wide
tags: [leetcode, tree, easy]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/)  
> Given an array where elements are sorted in ascending order, convert it to a height balanced BST. For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.



----------------------------
- 要求： 
给一个有序数组，将其用BST 表示




--------------------------
- 返回：  
binary search tree

----------------------------

- 例子：
	- input: [-10,-3,0,5,9]
	- output: one possible answer [0,-3,9,-10,null,5]  


----------------------------

## Solution
Recursive 的思想，由于BST的左右子树也是 BST, 确立array的中间点为root, 然后将左右子树 recursively表示成bst.

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def sortedArrayToBST(self, nums):
        """
        :type nums: List[int]
        :rtype: TreeNode
        """
        
        if len(nums) == 0:
            return None
			
        mid = len(nums) // 2
        bst = TreeNode(nums[mid])
        bst.left = self.sortedArrayToBST(nums[:mid])
        bst.right = self.sortedArrayToBST(nums[mid + 1:])
		
        return bst
```