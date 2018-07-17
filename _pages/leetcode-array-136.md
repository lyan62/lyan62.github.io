---
permalink: /leetcode/array/136
layout: single
classes: wide
title:  "136 Single number"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---

>  [Original Description](https://leetcode.com/problems/single-number/description/):
>  Given a non-empty array of integers, every element appears twice except for one. Find that single one.
>  Note: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

----------------------------
- 要求：
给一个数组，其中的元素只有一个出现一次，其余均出现两次，找出光棍。

--------------------------
- 返回：
光棍元素

----------------------------

- 例子：
	- input:  [2,2,1]
	- output: 1

----------------------------
## Solution
光棍的值 = set内元素之和x2 - 数组元素之和
```python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sum(set(nums))*2-sum(nums)
        # or can use dict to save count
```