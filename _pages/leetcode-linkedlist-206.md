---
permalink: /leetcode/linkedlist/206
layout: single
classes: wide
title:  "206 Reverse Linked List"
tags: [leetcode, array]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/reverse-linked-list/description/):
> Reverse a singly linked list.


----------------------------
- 要求：  
reverse 一个单向链表


--------------------------
- 返回：
reverse后的链表

----------------------------

- 例子：
	- input: 1->2->3->4->5->NULL
	- output: 5->4->3->2->1->NULL
	
----------------------------

## Solution
设置prev,每走一步，将指向next改为指向prev.

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        if head == None:
            return []
        else:
            prev = None
            curr = head
            after = head.next

            while after != None:
                after = curr.next
                curr.next = prev
                prev = curr
                curr = after
                after = after.next

            curr.next = prev 
            return curr
            
            
```