---
permalink: /leetcode/linkedlist/234
layout: single
classes: wide
tags: [leetcode, array]
title:  "234 Palindrome Linked List"
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/palindrome-linked-list/description/):
> Given a singly linked list, determine if it is a palindrome.

----------------------------
- 要求：  
判断链表中的值是否构成回文
	- O(n) time, O(1) space


--------------------------
- 返回：
True/False

----------------------------

- 例子：
	- input: 1->2->2->1
	- output: True
	
----------------------------

## Solution
首先利用快慢指针法找链表的中点， 以中点为head将后半段reverse, 判断reverse的后半段是否和前半段一致。

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def isPalindrome(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        if not head or not head.next:
            return True

        # slow and fast pointers
        slow = fast = head
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next

        slow = slow.next # slow指向链表的后半段
        slow = self.reverseList(slow)

        while slow:
            if head.val != slow.val:
                return False
            slow = slow.next
            head = head.next
        return True

    def reverseList(self, head):
        new_head = None
        while head:
            p = head
            head = head.next
            p.next = new_head
            new_head = p
        return new_head
```



