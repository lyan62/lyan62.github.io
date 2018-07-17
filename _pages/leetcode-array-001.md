---
permalink: /leetcode/array/001
layout: single
classes: wide
title:  "001 Two sum"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/two-sum/description/):
>  Given an array of integers, return indices of the two numbers such that they add up to a specific target.
>  You may assume that each input would have exactly one solution, and you may not use the same element twice.  

----------------------------
- 要求： 
给一个数组和目标和，求数组内相加等于目标和的两个元素的index。
	-  题目假设有唯一解，元素不可重复使用

--------------------------
- 返回：
index

----------------------------

- 例子：
	- input:  [2, 7, 11, 15], target = 9
	- output: [0,1]

----------------------------
## Solution
使用dict存储元素坐标，如果**目标和减去当前值**在字典中，返回其坐标和当前值坐标，否则将当前值及其坐标更新入dict.

```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        lookup = {}
        for i, num in enumerate(nums):
            if target - num in lookup:
                return [lookup[target - num], i]
            lookup[num] = i
        return []
```