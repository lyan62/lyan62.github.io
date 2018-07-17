---
permalink: /leetcode/array/026
layout: single
classes: wide
title:  "026 Remove duplicates from sorted array"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---





----------------------------
> [Original description](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/):    
>   Given a sorted array nums, remove the duplicates **in-place** such that each element appear only once and return the new length.
> 	Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

----------------------------
- 要求：
给一个有序数组，除去重复元素。使得该数组中每个元素仅出现一次。
	- inplace, with O(1) extra memory.

--------------------------
- 返回：
处理后数组的长度

----------------------------

- 例子：
	- input:  [1,1,2]
	- output: 2

----------------------------
## Solution
使用P1,P2一前一后从左往右，如果P2所指的元素与P1所指元素相同，从数组中POP P2所指元素。
```python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums == []:
            return 0
        elif len(nums) == 1:
            return 1
        else:    
            p1 = 0
            p2 = 1
            while p2<len(nums):
                if nums[p2] == nums[p1]:
                    nums.pop(p2)
                else:
                    p1+=1
                    p2+=1
            return len(nums)
```

