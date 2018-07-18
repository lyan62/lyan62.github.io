---
permalink: /leetcode/linkedlist/019
layout: single
classes: wide
title:  "019 Remove Nth Node From End of List"
tags: [leetcode, linkedlist, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/):
> Given a linked list, remove the n-th node from the end of list and return its head.


----------------------------
- 要求：  
给一个整数 n ,删掉链表中倒数第 n 个节点


--------------------------
- 返回：
返回删去后的链表

----------------------------

- 例子：
	- input: 1->2->3->4->5, n = 2
	- output: 1->2->3->5.
	
----------------------------

## Solution
使用两个指针 p1 p2，让 p1 先走 n 步，再让 p1 p2同时走，则当 p1走到末尾时，p2走到需要删除的节点。删除该节点即可。

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        # use two pointers
        # https://www.cnblogs.com/zuoyuan/p/3701971.html
		
        dummy=ListNode(0)
		dummy.next=head
        p1=p2=dummy
		
        for i in range(n): 
            p1=p1.next
        while p1.next:
            p1=p1.next; p2=p2.next
			
        p2.next=p2.next.next
        return dummy.next
```