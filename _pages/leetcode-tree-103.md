---
title: "103 Binary Tree Zigzag Level Order Traversal"
permalink: /leetcode/tree/103
layout: single
classes: wide
tags: [leetcode, tree, medium]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/)  
> Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).



----------------------------
- 要求： 
给一个binary tree， do zigzag level traversal.




--------------------------
- 返回：  
traversal 返回的数组

----------------------------

- 例子：
	- input: [3,9,20,null,null,15,7]
。    3
。   / \
。  9  20
。。   /  \
。。15   7
	- output: 
[ [3],
  [20,9],
  [15,7]]


----------------------------

## Solution
Referred to [shenjie's answer](https://shenjie1993.gitbooks.io/leetcode-python/103%20Binary%20Tree%20Zigzag%20Level%20Order%20Traversal.html):  
> 这道题跟 Binary Tree Level Order Traversal 非常相似，本质上也是树的广度优先遍历，只是在遍历的时候每一层的遍历顺序不同。那么我们只要一个变量来区分当前层是从前往后还是从后往前遍历: 当要反过来遍历节点时直接把原有的列表翻转了，而没有在生成列表的时候倒过来添加。

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def zigzagLevelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        
        result = []
        if not root:
            return result
        curr_level = [root]
        need_reverse = False
        while curr_level:
            level_result = []
            next_level = []
            for temp in curr_level:
                level_result.append(temp.val)
                if temp.left:
                    next_level.append(temp.left)
                if temp.right:
                    next_level.append(temp.right)
            if need_reverse:
                level_result.reverse()
                need_reverse = False
            else:
                need_reverse = True
            result.append(level_result)
            curr_level = next_level
        return result
```