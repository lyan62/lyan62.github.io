---
title: "116 Populating Next Right Pointers in Each Node"
permalink: /leetcode/tree/116
layout: single
classes: wide
tags: [leetcode, tree, medium]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/)  
> Given a binary tree
struct TreeLinkNode {
  TreeLinkNode *left;
  TreeLinkNode *right;
  TreeLinkNode *next;
}
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.  
Initially, all next pointers are set to NULL.



----------------------------
- 要求： 
给一个binary tree, 产生指向右边邻居的指针




--------------------------
- 返回：  
加入指向右侧指针的树结

----------------------------

- 例子：
	- input:      
	 1
   /  \
  2    3
 / \  / \
4  5  6  7
	- output:   
     1 -> NULL
   /  \
  2 -> 3 -> NULL
 / \  / \
4->5->6->7 -> NULL


----------------------------

## Solution
- solution 1: 比较brute-force的解法， 首先向右的指针是在每一level产生的， 所以进行level order traversal，将traversal的节点保存在list. 再用right pointer 链接每一个list里面的元素。
- solution 2: 如果有左右子树， 左子树节点 -> 右子树节点，如果当前root 有 .next指针，则右子树节点指向 .next 所指节点的左子树节点。 Do it recursively.

```python
# Definition for binary tree with next pointer.
# class TreeLinkNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
#         self.next = None

class Solution:
    # @param root, a tree link node
    # @return nothing
    def connect(self, root):
        node_list = self.levelOrder(root)
        for nl in node_list:
            if len(nl) == 1:
                nl[0].next = None
            else:
                for i in range(len(nl)-1):
                    if nl[i]!=nl[-1]:
                        nl[i].next = nl[i+1]
                    else:
                        nl[i].next = None
        
        
    
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
        res[depth].append(root)
        self.dfs(root.left, depth+1, res)
        self.dfs(root.right, depth+1, res)
        
        
### simpler answer in discuss
#      if not root:
#         return None
    
#     if not root.left and not root.right:
#         return None
    
#     root.left.next = root.right
#     if root.next:
#         root.right.next = root.next.left
    
#     self.connect(root.left)
#     self.connect(root.right)
```