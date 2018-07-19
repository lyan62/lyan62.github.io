---
permalink: /leetcode/array/035
layout: single
classes: wide
title:  "035 Search Insert Position"
tags: [leetcode, array, easy]
date:   2018-07-19
sidebar:
  nav: "leetcode"
---



>  [Original Description](https://leetcode.com/problems/search-insert-position/description/):
> Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
You may assume no duplicates in the array.


----------------------------
- 要求：
给一个有序数组，和一个数，输出一个index
	-  如果数组中有该数，返回对应index
	-  否则，返回应该插入该数的index



--------------------------
- 返回：
index

----------------------------

- 例子：
	- input: [1,3,5,6]， val= 5
	- output: 2
	
----------------------------

## Solution
从左到右遍历数组，使用一个stack存储目前最佳位置，如果当前数比target小，则pop前一个stack保存的位置,保存 当前index+1 。  如果当前值等于目标值， 返回当前 index.

```python
class Solution:
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        stack = [0]
        for i in range(len(nums)):
            if nums[i] == target:
                return i
            elif nums[i] < target:
                stack.pop()
                stack.append(i+1)
                
        return stack[0]
```



