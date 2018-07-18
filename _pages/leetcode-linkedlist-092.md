---
permalink: /leetcode/linkedlist/092
layout: single
classes: wide
title:  "092 Reverse a single sublist"
tags: [leetcode, array]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---

An extension of [Reverse Linkedlist](https://lyan62.github.io/leetcode/linkedlist/206).
>  [Original Description](https://leetcode.com/problems/reverse-linked-list-ii/description/):
> Reverse a linked list from position m to n. Do it in one-pass.


----------------------------
- 要求：  
一个单向链表，reverse 其中 m 到 n 位置的节点
	-	1 ≤ m ≤ n ≤ length of list.
	- 要求只能遍历一遍


--------------------------
- 返回：
reverse后的链表

----------------------------

- 例子：
	- input: 1->2->3->4->5->NULL, m = 2, n = 4
	- output: 1->4->3->2->5->NULL
	
----------------------------

## Solution

先走$$m$$ 步到当前节点curr,保留curr, prev的备份用于后续链接reverse的节点。
再利用 $$n-m$$ 步进行reverse.
Note: brute force提取 m ~ n 段节点，reverse,再链接回，会超时。

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseBetween(self, head, m, n):
        """
        :type head: ListNode
        :type m: int
        :type n: int
        :rtype: ListNode
        """
        dummy = ListNode(0)
        dummy.next = head
        curr = dummy.next
        prev = dummy
        
        for i in range(m-1):
            prev = curr
            curr = curr.next
        
        prev_copy = prev
        curr_copy = curr
        for i in range(n-m):
            after = curr.next
            curr.next = prev
            prev = curr
            curr = after
    
        after = curr.next
        curr.next = prev
        prev_copy.next = curr
        curr_copy.next = after
        
        return dummy.next           
```

-------------------------------
### EPI 的解法：
思路同上，但是code更简洁

```python
class Solution(object):
    def reverseBetween(self, head, m, n):
        """
        :type head: ListNode
        :type m: int
        :type n: int
        :rtype: ListNode
        """
        dummy_head = sublist_head = ListNode(0)
        sublist_head.next = dummy_head.next = head
        for i in range(1,m):
            sublist_head = sublist_head.next
		
        # reverse sublist
        sublist_iter = sublist_head.next
        for i in range(n-m):
            tmp = sublist_iter.next
            sublist_iter.next, tmp.next, sublist_head.next = (tmp.next, sublist_head.next, tmp)
        
        return dummy_head.next
```