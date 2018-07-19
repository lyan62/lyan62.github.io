---
permalink: /leetcode/array/027
layout: single
classes: wide
title:  "027 Remove Element"
tags: [leetcode, array, easy]
date:   2018-07-19
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/remove-element/description/):
> Given an array nums and a value val, remove all instances of that value in-place and return the new length.  
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
The order of elements can be changed. It doesn't matter what you leave beyond the new length.


----------------------------
- 要求：  
给一个数组，和值val,除去数组中与val相同的元素


--------------------------
- 返回：
除去元素后的数组长度

----------------------------

- 例子：
	- input: nums = [3,2,2,3]， val= 3
	- output: 2
	
----------------------------

## Solution
从数组末端开始，使用前后两个指针，将与val等值的元素置换到数组最后。

```python
class Solution:
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        # swap numbers that equal to val into the end of the array
        j = len(nums)-1
        for i in range(len(nums) - 1, -1, -1):
            if nums[i] == val:
                nums[i], nums[j] = nums[j], nums[i]
                j -= 1
        return j+1
```



