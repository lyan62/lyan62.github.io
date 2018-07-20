---
permalink: /leetcode/array/167
layout: single
classes: wide
title: "167 Two Sum II - Input array is sorted"
tags: [leetcode, array, easy]
date:   2018-07-20
sidebar:
  nav: "leetcode"
---

>  [Original Description](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/):
> Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.  
> The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.   
> Note: 
> - Your returned answers (both index1 and index2) are not zero-based.  
> - You may assume that each input would have exactly one solution and you may not use the same element twice.


----------------------------
- 要求： 
给一个有序数组，和一个target, 返回其中两个和为target的元素的位置 (index)。
	- note: 数组index不是从0开始的




--------------------------
- 返回：
index

----------------------------

- 例子：
	- input: [2,7,11,15], target = 9
	- output: [1,2]


----------------------------

## Solution
-  可以用与 [001 Two Sum](https://lyan62.github.io/leetcode/array/001) 相同的解法， 即用dict保存元素坐标，判断**目标和减去当前值** 是否在dict中， 有则返回坐标，无则存储当前元素:坐标。 
-  由于序列有序，可以使用两个指针从两边向中间逼近。

这里用dict解法。
```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        
        lookup = {}
        for i, num in enumerate(nums):
            if target - num in lookup:
                return [lookup[target - num]+1, i+1]
            lookup[num] = i
        return []
```



