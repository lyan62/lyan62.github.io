---
permalink: /leetcode/linkedlist/
layout: single
classes: wide
title:  "Linked List"
tags: [leetcode, linkedList]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


---------------------------
Definition of singly-linked list.  
Each node contains two fields: val, next.
```python
class ListNode(object):
    def __init__(self, x):
        self.val = x
        self.next = None
```
----------------------------------

Insertion & Deletion cost $$O(1)$$ time. While search costs $$O(n)$$ time, where $$n$$ is the length of the list.
Basic operations of linked list can be defined with functions:  
```python
def search_list(L,key):
    while L and L.val != key:
        L = L.next
    return L
    
def insert_after(node, new_node):
    new_node.next = node.next
    node.next = new_node

def delete_after(node):
    node.next = node.next.next
``` 
------------------------------------
Tricks:
- 通常关于链表的题目，采用两个指针（two iterators）:  
    - 一前一后
    - 一快一慢
- 使用dummy head
    ```python
    dummy = ListNode(0)
    dummy.next = head
    ```
------------------------------------

Problems listed in the order of difficulty. * denotes in top interview questions.

# Easy
- 019 019 Remove Nth Node From End of List * ([note](https://lyan62.github.io/leetcode/linkedlist/019))
- 237 Delete Node in a Linked List * ([note](https://lyan62.github.io/leetcode/linkedlist/237))
