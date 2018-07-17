---
permalink: /leetcode/array/217
layout: single
classes: wide
title:  "217 Contains duplicates"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/contains-duplicate/description/):
>  Given an array of integers, find if the array contains any duplicates.
>  Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

----------------------------
- 要求：
给一个数组，判断其是否中是否含有重复元素

--------------------------
- 返回：
True/False

----------------------------

- 例子：
	- input:  [1,2,3,1]
	- output: True

----------------------------
## Solution
option 1: 如果set()的长度小于数组长度，则有重复;（code in comment）；  
option 2: 使用dictionary, 遍历数组，判断是否在dict中。
```python
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        ##### sol1: use set()
        # if len(set(nums)) < len(nums):
        #     return True
        # else:
        #     return False
        
        ##### sol2: use dict()
        c = dict()
        flag = False
        for n in nums:
            if n not in c: 
                c[n] = 1
            else:
                flag = True
        return flag
```
