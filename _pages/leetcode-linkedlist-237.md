---
permalink: /leetcode/linkedlist/237
layout: single
classes: wide
title:  "237 Delete Node in a Linked List"
tags: [leetcode, array]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---



>  [Original Description](https://leetcode.com/problems/delete-node-in-a-linked-list/description/):
>  Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.


----------------------------
- 要求：  
给一个节点，删掉该节点。


--------------------------
- 返回：
无需返回

----------------------------

- 例子：
	- input: head = [4,5,1,9], node = 5
	- output: [4,1,9]
	
----------------------------

## Solution
把下一个节点的指针和值都给当前节点即可。

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution(object):
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        next_node = node.next
        node.val = next_node.val
        node.next = next_node.next
```