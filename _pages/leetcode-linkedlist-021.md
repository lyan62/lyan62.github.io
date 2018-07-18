---
permalink: /leetcode/linkedlist/021
layout: single
classes: wide
title:  "021 Merge Two Sorted Lists"
tags: [leetcode, array]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/merge-two-sorted-lists/description/):
> Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.


----------------------------
- 要求：  
merge 两个**有序**的链表


--------------------------
- 返回：
merge 后的链表

----------------------------

- 例子：
	- input: 1->2->4, 1->3->4
	- output: 1->1->2->3->4->4
	
----------------------------

## Solution
- Recursive: 比较 l1 和 l2 head 的值， 若 l1.val <= l2.val, 将 l1设为 head,继续 merge l2 和 l1的剩余部分。

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeTwoLists(self, l1, l2):

        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        # recursively
        
        if l1 == None:
            return l2
        if l2 == None:
            return l1
            
        if l1.val <= l2.val:
            head = l1 
            head.next = self.mergeTwoLists(l1.next, l2)
        else:
            head = l2
            head.next = self.mergeTwoLists(l1, l2.next)
        
        return head 
```

- EPI iterative 解法：
遍历两个链表，比较值， 始终选择value较小的继续遍历。

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeTwoLists(self, l1, l2):

        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        # iterative
        dummy_head = tail = ListNode()
        
        while l1 and l2:
            if l1.val < l2.val:
                tail.next, l1 = l1, l1.next
            else:
                tail.next, l2 = l2, l2.next
            tail = tail.next
        # appends remaining nodes of l1 or l2
        tail.next = l1 or l2
        return dummy_head.next
```

