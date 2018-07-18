---
permalink: /leetcode/linkedlist/141
layout: single
classes: wide
tags: [leetcode, linkedlist, easy]
title:  "141 Linked List Cycle"
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/linked-list-cycle/description/):
> Given a linked list, determine if it has a cycle in it.
> without using extra space?

----------------------------
- 要求：  
判断所给链表是否构成环


--------------------------
- 返回：
True/False

----------------------------

- 例子：
	- input: 1->2->3->1
	- output: True
	
----------------------------

## Solution
利用快慢指针法, 快的一次走两步，慢的一次走一步，如果有环两指针必于某一时刻相遇，否则其中之一会到达none.

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        # http://oj.leetcode.com/problems/linked-list-cycle/
        
        fast, slow = head, head
        if not head:
            return False
        while fast.next and slow.next:
            slow = slow.next
            fast = fast.next.next
            if not fast:
                return False
            if fast == slow:
                return True
        return False
```



